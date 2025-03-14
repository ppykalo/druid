# Changelog

The latest published Druid release is [0.7.0](#070---2021-01-01) which was released on 2021-01-01.
You can find its changes [documented below](#070---2021-01-01).

## Unreleased

### Highlights

- International text input support (IME) on macOS.
- Rich text and complex script support on Linux.

### Added

- Strikethrough rich text attribute ([#1953] by [@jenra-uwu])
- System fonts loaded so that SVG images render text ([#1850] by [@DrGabble])
- Add `scroll()` method in WidgetExt ([#1600] by [@totsteps])
- `write!` for `RichTextBuilder` ([#1596] by [@Maan2003])
- Sub windows: Allow opening windows that share state with arbitrary parts of the widget hierarchy ([#1254] by [@rjwittams])
- WindowCloseRequested/WindowDisconnected event when a window is closing ([#1254] by [@rjwittams])
- Add `on_added()` method in `WidgetExt` ([#1485] by [@arthmis])
- RichTextBuilder ([#1520] by [@Maan2003])
- `get_external_handle` on `DelegateCtx` ([#1526] by [@Maan2003])
- `AppLauncher::localization_resources` to use custom l10n resources. ([#1528] by [@edwin0cheng])
- Shell: get_content_insets and mac implementation ([#1532] by [@rjwittams])
- Contexts: to_window and to_screen (useful for relatively positioning sub windows) ([#1532] by [@rjwittams])
- WindowSizePolicy: allow windows to be sized by their content ([#1532] by [@rjwittams])
- Implemented `Data` for more datatypes from `std` ([#1534] by [@derekdreery])
- Shell: windows implementation from content_insets ([#1592] by [@HoNile])
- Support individual corner radii for kurbo::RoundedRect ([#1561] by [@SecondFlight])
- Shell: IME API and macOS IME implementation ([#1619] by [@lord])
- Scroll::content_must_fill and a few other new Scroll methods ([#1635] by [@cmyr])
- New `TextBox` widget with IME integration ([#1636] by [@cmyr])
- `Notification`s can be submitted while handling other `Notification`s ([#1640] by [@cmyr])
- Added ListIter implementations for OrdMap ([#1641] by [@Lejero])
- Add `AspectRatioBox` widget ([#1645] by [@arthmis])
- `Padding` can now use `Key<Insets>` ([#1662] by [@cmyr])
- `LifeCycle::DisabledChanged`, `InternalLifeCycle::RouteDisabledChanged` and the `set_disabled()` and `is_disabled()`
  context-methods to implement disabled ([#1632] by [@xarvic])
- `LifeCycle::BuildFocusChain` to update the focus-chain ([#1632] by [@xarvic])
- `DisabledIf` widget wrapper to disable based on the state of Data and Env ([#1702] by [@xarvic])
- GTK: added support for `content_insets` ([#1722] by [@jneem])
- `chrono` feature with `Data` support for [chrono](https://docs.rs/chrono/) types ([#1743] by [@r-ml])
- Text input handles Delete key ([#1746] by [@bjorn])
- `lens` macro can access nested fields ([#1764] by [@Maan2003])
- X11 backend now supports custom cursors ([#1801] by [@psychon])
- X11: Add support for transparent windows ([#1803] by [@psychon])
- X11: Added support for `get_monitors` ([#1804] by [@psychon])
- x11: Remove some unnecessary casts ([#1851] by [@psychon])
- `has_focus` method on `WidgetPod` ([#1825] by [@ForLoveOfCats])
- x11: Add support for getting and setting clipboard contents ([#1805], [#1851], and [#1866] by [@psychon])
- Linux extension: primary_clipboard ([#1843] by [@Maan2003])
- x11: Implement primary_clipboard ([#1867] by [@psychon])
- x11: Set WM_CLASS property ([#1868] by [@psychon])
- Expose `RawWindowHandle` for `WindowHandle` under the `raw-win-handle` feature ([#1828] by [@djeedai])
- `Slider` widget now warns if max < min and swaps the values ([#1882] by [@Maan2003])
- Widget/Slider: Add stepping functionality ([#1875] by [@raymanfx])
- Add #[data(eq)] shorthand attribute for Data derive macro ([#1884] by [@Maan2003])
- X11: detect keyboard layout ([#1779] by [@Maan2003])
- WindowDesc::with_config ([#1929] by [@Maan2003])
- `scroll_to_view` and `scroll_area_to_view` methods on `UpdateCtx`, `LifecycleCtx` and `EventCtx` ([#1976] by [@xarvic])
- `Notification::route` ([#1978] by [@xarvic])
- Build on OpenBSD ([#1993] by [@klemensn])
- Scope: expose scoped state using state() and state_mut() ([#2082] by [@rjwittams]
- Tabs: allow getting and setting the tab index of a Tabs widget ([#2082] by [@rjwittams]
- `RangeSlider` and `Annotated` ([#1979] by [@xarvic])
- Add `Checkbox::from_label` constructor ([#2111] by [@maurerdietmar])
- fix content_insets for gtk backend ([#2117] by [@maurerdietmar])
- `ClipBox::managed`, `Notification::warn_if_ununsed` and `Notification::warn_if_ununsed_set` ([#2141] by [@xarvic])
- `ClipBox` and `Tabs` handle SCROLL_TO_VIEW ([#2141] by [@xarvic])
- `EventCtx::submit_notification_without_warning` ([#2141] by [@xarvic])
- `WidgetPod::requested_layout` ([#2145] by [@xarvic])
- Make `Parse` work better with floats and similar types ([#2148] by [@superfell])
- Added `compute_max_intrinsic` method to the `Widget` trait, which determines the maximum useful dimension of the widget ([#2172] by [@sjoshid])
- Windows: Dark mode support for the title bar ([#2196] by [@dristic])
- `ZStack` widget ([#2235] by [@xarvic])
- `Lifecycle::ViewStateChanged`, `InternalLifecycle::RouteViewStateChanged`, `ChangeCtx`, and `RequestCtx` ([#2149] by [@xarvic])
- Add a public constructor to `StringCursor` ([#2319] by [@benoitryder])

### Changed

- ~~Warn on unhandled Commands ([#1533] by [@Maan2003])~~ (Reverted in #1813)
- `WindowDesc::new` takes the root widget directly instead of a closure ([#1559] by [@lassipulkkinen])
- Switch to trace-based logging ([#1562] by [@PoignardAzur])
- Spacers in `Flex` are now implemented by calculating the space in `Flex` instead of creating a widget for it ([#1584] by [@JAicewizard])
- Padding is generic over child widget, impls WidgetWrapper ([#1634] by [@cmyr])
- Menu support was rewritten with support for `Data` ([#1625] by [@jneem])
- Update to piet v0.4.0 (rich text on linux!) ([#1677] by [@cmyr])
- `register_for_focus()` should from now on be called from `LifeCycle::BuildFocusChain` instead of `LifeCycle::WidgetAdded` ([#1632] by [@xarvic])
- Flex values that are less than 0.0 will default to 0.0 and warn in release. It will panic in debug mode. ([#1691] by [@arthmis])
- Lens implemented for tuples of Lenses of length 2-8, Tuple2 removed ([#1654] by [@Maan2003])
- Window size and positioning code is now in display points ([#1713] by [@jneem])
- Update look and feel of controls when disabled ([#1717] by [@xarvic])
- Change the signature of `add_idle_callback` ([#1787] by [@jneem])
- Move macOS only function to Mac extension trait ([#1863] by [@Maan2003])
- x11: Only query atoms once instead of per window ([#1865] by [@psychon])
- remove prefix from platform extension traits ([#1873] by [@Maan2003])
- Remove `set_level` on windows ([#1919] by [@JAicewizard])
- Add parent windows to non-main windows. (Coordinate space is now from their origin) ([#1919] by [@JAicewizard])
- `ListIter` implementations for `Arc<Vec<T>>`, `(S, Arc<Vec<T>>)`, `Arc<VecDequeue<T>>` and `(S, Arc<VecDequeue<T>>)` ([#1967] by [@xarvic])
- Closures passed to `Label::new` can now return any type that implements `Into<ArcStr>` ([#2064] by [@jplatte])
- `AppDelegate::window_added` now receives the new window's `WindowHandle`. ([#2119] by [@zedseven])
- Removed line of code that prevented window miximalization. ([#2113] by [@Pavel-N])
- Dont warn about unhandled `Notification`s which have `known_target` set to false ([#2141] by [@xarvic])
- `ClipBox`, `Flex`, `List` and `Split` only call layout on children which need it ([#2145] by [@xarvic])
- `SizedBox` now supports using `Key<f64>` for specifying  size ([#2151] by [@GoldsteinE])
- `RadioGroup` widgets are now constructed with new `row()`, `column()`, and `for_axis()` methods ([#2157] by [@twitchyliquid64])
- Replace `info_span!` with `trace_span!` ([#2203] by [@NickLarsenNZ])
- `WidgetPod::event` propagates handled mouse events to active children ([#2235] by [@xarvic])
- changing hot state is now done in `Lifecycle::ChangeViewState` instead of `layout` ([#2149] by [@xarvic])
- `WidgetPod::set_origin` no longer takes `data` and `env` as parameters. ([#2149] by [@xarvic])

### Deprecated

### Removed

- Remove Default impl for `FlexParams` ([#1885] by [@Maan2003])

### Fixed

- Centre checkmark in checkbox ([#2036] by [@agentsim])
- `Notification`s will not be delivered to the widget that sends them ([#1640] by [@cmyr])
- `TextBox` can handle standard keyboard shortcuts without needing menus ([#1660] by [@cmyr])
- GTK Shell: Prevent mangling of newline characters in clipboard ([#1695] by [@ForLoveOfCats])
- GTK: Replaced call to `std::str::from_utf8_unchecked` with `from_utf8` ([#1820] by [@psychon])
- Use correct fill rule when rendering SVG paths ([#1606] by [@SecondFlight])
- Correctly capture and use stroke properties when rendering SVG paths ([#1647] by [@SecondFlight])
- focus-chain now only includes non hidden (`should_propagate_to_hidden()` on `Event` and `Lifecylce`) widgets ([#1724] by [@xarvic])
- Fixed layout of scrollbar with very small viewports ([#1715] by [@andrewhickman])
- Fixed `WindowLevel::Tooltip` on Windows platform ([#1737] by [@djeedai])
- X11 backend now supports scaling([#1751] by [@Maan2003])
- X11 backend now supports changing cursors ([#1755] by [@Maan2003])
- X11 backend now uses the platform locale ([#1756] by [@Maan2003])
- `Either` and `Tab` widgets were still propagating events to hidden widgets ([#1860] by [@lisael])
- RichText: Invalidate layout on Env change ([#1907] by [@Maan2003])
- GTK: fix using gdk before initialising it ([#1946] by [@JAicewizard])
- `ListIter` implementations for `Vector<T>` and `(S, Vector<T>)` ([#1967] by [@xarvic])
- Do not panic in Application::try_global if Application is not created ([#1996] by [@Maan2003])
- X11: window focus events ([#1938] by [@Maan2003]
- Preserve the aspect ratio of a clipped region in an Image ([#2195] by [@barsae])
- GTK: Hot state now properly resets when the mouse leaves the window via an occluded part. ([#2324] by [@xStrom])

### Visual

### Docs

- Fixed docs of derived Lens ([#1523] by [@Maan2003])
- Fixed docs describing `ViewSwitcher` widget functionality ([#1693] by [@arthmis])
- Added missing documentation on derived lens items ([#1696] by [@lidin])
- Fix example code in `Get started with Druid` chapter of book ([#1698] by [@ccqpein])
- Fix link in documentation of widget::Image ([#1730] by [@RichardPoole42])
- Added more detailed explanation of `Target::Auto` ([#1761] by [@arthmis])
- Updated source code, tests and docs to use `Selector::with` instead of `Command::new` ([#1761] by [@arthmis])
- Updated docs of `should_propagate_to_hidden`, `children_changed` and `register_for_focus` ([#1861] by [@xarvic])
- Update docs of `RawLabel`: does not require `ArcStr`([#1886] by [@Maan2003])
- Fix `Controller` links for `Click` ([#2158] by [@yrns])
- Delete inaccurate line for `KeyEvent` ([#2247] by [@amtep])
- Added examples in `TextBox` ([#2284] by [@ThomasMcandrew])
- Removed outdated section in docs for `LifeCycle::WidgetAdded` ([#2320] by [@sprocklem])
- Updated `Event::AnimFrame` docs with info about when `paint` happens. ([#2323] by [@xStrom])

### Examples
- Add readme ([#1423] by [@JAicewizard])

### Maintenance

- Updated to x11rb 0.8.0. ([#1519] by [@psychon])
- Updated fluent-bundle to 0.15.1 and fluent syntax to 0.11.0 ([#1772] by [@r-ml])
- Updated usvg to 0.14.1 ([#1802] by [@r-ml])
- x11: Add logging to `Application::get_locale` ([#1876] by [@Maan2003])
- Converted all calls of `approx_eq!` in tests to `assert_approx_eq!` ([#2331] by [@cbondurant])

### Outside News

## [0.7.0] - 2021-01-01

### Highlights

- Text improvements: `TextLayout` type ([#1182]) and rich text support ([#1245])
- The `Formatter` trait provides more flexible handling of conversions between
values and their textual representations. ([#1377])

### Added

- Windows: Added Screen module to get information about monitors and the screen. ([#1037] by [@rhzk])
- Added documentation to resizable() and show_titlebar() in WindowDesc. ([#1037] by [@rhzk])
- Windows: Added internal functions to handle Re-entrancy. ([#1037] by [@rhzk])
- Windows: WindowDesc: Create window with disabled titlebar, maximized or minimized state, and with position. ([#1037] by [@rhzk])
- Windows: WindowHandle: Change window state. Toggle titlebar. Change size and position of window. ([#1037], [#1324] by [@rhzk])
- Windows: WindowHandle: Added handle_titlebar(), Allowing a custom titlebar to behave like the OS one. ([#1037] by [@rhzk])
- `OPEN_PANEL_CANCELLED` and `SAVE_PANEL_CANCELLED` commands. ([#1061] by @cmyr)
- Export `Image` and `ImageData` by default. ([#1011] by [@covercash2])
- Re-export `druid_shell::Scalable` under `druid` namespace. ([#1075] by [@ForLoveOfCats])
- `TextBox` now supports ctrl and shift hotkeys. ([#1076] by [@vkahl])
- `ScrollComponent` for ease of adding consistent, customized, scrolling behavior to a widget. ([#1107] by [@ForLoveOfCats])
- Selection text color to textbox. ([#1093] by [@sysint64])
- `BoxConstraints::UNBOUNDED` constant. ([#1126] by [@danieldulaney])
- Close requests from the shell can now be intercepted ([#1118] by [@jneem], [#1204] by [@psychon], [#1238] by [@tay64])
- The Lens derive now supports an `ignore` attribute. ([#1133] by [@jneem])
- `request_update` in `EventCtx`. ([#1128] by [@raphlinus])
- `ExtEventSink`s can now be obtained from widget methods. ([#1152] by [@jneem])
- 'Scope' widget to allow encapsulation of reactive state. ([#1151] by [@rjwittams])
- `Ref` lens that applies `AsRef` and thus allow indexing arrays. ([#1171] by [@finnerale])
- `Command::to` and `Command::target` to set and get a commands target. ([#1185] by [@finnerale])
- `Menu` commands can now choose a custom target. ([#1185] by [@finnerale])
- `Movement::StartOfDocument`, `Movement::EndOfDocument`. ([#1092] by [@sysint64])
- `TextLayout` type simplifies drawing text ([#1182] by [@cmyr])
- Added support for custom mouse cursors ([#1183] by [@jneem])
- Implementation of `Data` trait for `i128` and `u128` primitive data types. ([#1214] by [@koutoftimer])
- `LineBreaking` enum allows configuration of label line-breaking ([#1195] by [@cmyr])
- `TextAlignment` support in `TextLayout` and `Label` ([#1210] by [@cmyr])
- `UpdateCtx` gets `env_changed` and `env_key_changed` methods ([#1207] by [@cmyr])
- `Button::from_label` to construct a `Button` with a provided `Label`. ([#1226] by [@ForLoveOfCats])
- Lens: Added Unit lens for type erased / display only widgets that do not need data. ([#1232] by [@rjwittams])
- `WindowLevel` to control system window Z order, with Mac and GTK implementations  ([#1231] by [@rjwittams])
- WIDGET_PADDING items added to theme and `Flex::with_default_spacer`/`Flex::add_default_spacer` ([#1220] by [@cmyr])
- CONFIGURE_WINDOW command to allow reconfiguration of an existing window. ([#1235] by [@rjwittams])
- Added a ClipBox widget for building scrollable widgets ([#1248] by [@jneem])
- `RawLabel` widget displays text `Data`. ([#1252] by [@cmyr])
- 'Tabs' widget allowing static and dynamic tabbed layouts. ([#1160] by [@rjwittams])
- `RichText` and `Attribute` types for creating rich text ([#1255] by [@cmyr])
- `request_timer` can now be called from `LayoutCtx` ([#1278] by [@Majora320])
- TextBox supports vertical movement ([#1280] by [@cmyr])
- Widgets can specify a baseline, flex rows can align baselines ([#1295] by [@cmyr])
- `TextBox::with_text_color` and `TextBox::set_text_color` ([#1320] by [@cmyr])
- `Checkbox::set_text` to update the label. ([#1346] by [@finnerale])
- `Event::should_propagate_to_hidden` and `Lifecycle::should_propagate_to_hidden` to determine whether an event should be sent to hidden widgets (e.g. in `Tabs` or `Either`). ([#1351] by [@andrewhickman])
- `set_cursor` can be called in the `update` method. ([#1361] by [@jneem])
- `WidgetPod::is_initialized` to check if a widget has received `WidgetAdded`. ([#1259] by [@finnerale])
- `TextBox::with_text_alignment` and `TextBox::set_text_alignment` ([#1371] by [@cmyr])
- Add default minimum size to `WindowConfig`. ([#1438] by [@colinfruit])
- Open and save dialogs send configurable commands. ([#1463] by [@jneem])
- Windows: Dialogs now respect the parameter passed to `force_starting_directory()` ([#1452] by [@MaximilianKoestler])
- Value formatting with the `Formatter` trait ([#1377] by [@cmyr])

### Changed

- Windows: Reduced flashing when windows are created on high-dpi displays ([#1272] by [@rhzk])
- Windows: Improved DPI handling. Druid should now redraw correctly when dpi changes. ([#1037] by [@rhzk])
- windows: Window created with OS default size if not set. ([#1037] by [@rhzk])
- `Scale::from_scale` to `Scale::new`, and `Scale` methods `scale_x` / `scale_y` to `x` / `y`. ([#1042] by [@xStrom])
- Major rework of keyboard event handling. ([#1049] by [@raphlinus])
- `Container::rounded` takes `KeyOrValue<f64>` instead of `f64`. ([#1054] by [@binomial0])
- `request_anim_frame` no longer invalidates the entire window. ([#1057] by [@jneem])
- Use new Piet text api ([#1143] by [@cmyr])
- `Env::try_get` (and related methods) return a `Result` instead of an `Option`. ([#1172] by [@cmyr])
- `lens!` macro to use move semantics for the index. ([#1171] by [@finnerale])
- `Env` stores `Arc<str>` instead of `String` ([#1173] by [@cmyr])
- Replaced uses of `Option<Target>` with the new `Target::Auto`. ([#1185] by [@finnerale])
- Moved `Target` parameter from `submit_command` to `Command::new` and `Command::to`. ([#1185] by [@finnerale])
- `Movement::RightOfLine` to `Movement::NextLineBreak`, and `Movement::LeftOfLine` to `Movement::PrecedingLineBreak`. ([#1092] by [@sysint64])
- `AnimFrame` was moved from `lifecycle` to `event` ([#1155] by [@jneem])
- Renamed `ImageData` to `ImageBuf` and moved it to `druid_shell` ([#1183] by [@jneem])
- Contexts' `text()` methods return `&mut PietText` instead of cloning ([#1205] by [@cmyr])
- Window construction: WindowDesc decomposed to PendingWindow and WindowConfig to allow for sub-windows and reconfiguration. ([#1235] by [@rjwittams])
- `LocalizedString` and `LabelText` use `ArcStr` instead of String ([#1245] by [@cmyr])
- `LensWrap` widget moved into widget module ([#1251] by [@cmyr])
- `Delegate::command` now returns `Handled`, not `bool` ([#1298] by [@jneem])
- `TextBox` selects all contents when tabbed to on macOS ([#1283] by [@cmyr])
- All Image formats are now optional, reducing compile time and binary size by default ([#1340] by [@JAicewizard])
- The `Cursor` API has changed to a stateful one ([#1433] by [@jneem])
- Part of the `SAVE_FILE` command is now `SAVE_FILE_AS` ([#1463] by [@jneem])
- Windows: Use custom application icon, if present ([#2274] by [@tay64])

### Deprecated
- Parse widget (replaced with `Formatter` trait) ([#1377] by [@cmyr])

### Removed

- `Scale::from_dpi`, `Scale::dpi_x`, and `Scale::dpi_y`. ([#1042] by [@xStrom])
- `Scale::to_px` and `Scale::to_dp`. ([#1075] by [@ForLoveOfCats])

### Fixed

- `ClipBox` should forward events if any child is active, not just the immediate child. ([#1448] by [@derekdreery])
- macOS: Timers not firing during modal loop. ([#1028] by [@xStrom])
- GTK: Directory selection now properly ignores file filters. ([#957] by [@xStrom])
- GTK: Don't crash when receiving an external command while a file dialog is visible. ([#1043] by [@jneem])
- `Data` derive now works when type param bounds are defined. ([#1058] by [@chris-zen])
- Ensure that `update` is called after all commands. ([#1062] by [@jneem])
- X11: Support idle callbacks. ([#1072] by [@jneem])
- GTK: Don't interrupt `KeyEvent.repeat` when releasing another key. ([#1081] by [@raphlinus])
- Floor the origin for the Align widget to avoid blurry borders. ([#1091] by [@sysint64])
- X11: Set some more common window properties. ([#1097] by [@psychon])
- X11: Support timers. ([#1096] by [@psychon])
- `EnvScope` now also updates the `Env` during `Widget::lifecycle`. ([#1100] by [@finnerale])
- `WidgetExt::debug_widget_id` and `debug_paint_layout` now also apply to the widget they are called on. ([#1100] by [@finnerale])
- X11: Fix X11 errors caused by destroyed windows. ([#1103] by [@jneem])
- `ViewSwitcher` now skips the update after switching widgets. ([#1113] by [@finnerale])
- Key and KeyOrValue derive Clone ([#1119] by [@rjwittams])
- Allow submit_command from the layout method in Widgets ([#1119] by [@rjwittams])
- Allow derivation of lenses for generic types ([#1120]) by [@rjwittams])
- Switch widget: Toggle animation being window refresh rate dependent ([#1145] by [@ForLoveOfCats])
- Multi-click on Windows, partial fix for #859 ([#1157] by [@raphlinus])
- Windows: fix crash on resize from incompatible resources ([#1191 by [@raphlinus]])
- GTK: Related dependencies are now optional, facilitating a pure X11 build. ([#1241] by [@finnerale])
- `widget::Image` now computes the layout correctly when unbound in one direction. ([#1189] by [@JAicewizard])
- TextBox doesn't reset position after unfocused. ([#1276] by [@sysint64])
- Able to select text in multiple TextBoxes at once. ([#1276] by [@sysint64])
- The scroll bar now shows when the contents of a scrollable area change size. ([#1278] by [@Majora320])
- Fix `widget::Either` using the wrong paint insets ([#1299] by [@andrewhickman])
- Various fixes to cross-platform menus ([#1306] by [@raphlinus])
- Improve Windows 7 DXGI compatibility ([#1311] by [@raphlinus])
- Fixed `Either` not passing events to its hidden child correctly. ([#1351] by [@andrewhickman])
- Don't drop events while showing file dialogs ([#1302], [#1328] by [@jneem])
- Ensure that `LifeCycle::WidgetAdded` is the first thing a widget sees. ([#1259] by [@finnerale])
- Fix a missed call to `CloseClipboard` on Windows. ([#1410] by [@andrewhickman])
- WidgetPod: change not laid out `debug_panic` to warning ([#1441] by [@Maan2003])

### Visual

- `TextBox` stroke remains inside its `paint_rect`. ([#1007] by [@jneem])

### Docs

- Added a book chapter about resolution independence. ([#913] by [@xStrom])
- Added documentation for the `Image` widget. ([#1018] by [@covercash2])
- Fixed a link in `druid::command` documentation. ([#1008] by [@covercash2])
- Fixed broken links in `druid::widget::Container` documentation. ([#1357] by [@StarfightLP])

### Examples

- Specify feature requirements in a standard way. ([#1050] by [@xStrom])
- Added `event_viewer` example ([#1326] by [@cmyr])
- Rename `ext_event` to `async_event`. ([#1401] by [@JAicewizard])

### Maintenance

- Standardized web targeting terminology. ([#1013] by [@xStrom])
- X11: Ported the X11 backend to [`x11rb`](https://github.com/psychon/x11rb). ([#1025] by [@jneem])
- Add `debug_panic` macro for when a backtrace is useful but a panic unnecessary. ([#1259] by [@finnerale])

### Outside News

## [0.6.0] - 2020-06-01

### Highlights

#### X11 backend for druid-shell.

[@crsaracco] got us started and implemented basic support to run druid on bare-metal X11 in [#599].
Additional features got fleshed out in [#894] and [#900] by [@xStrom]
and in [#920], [#961], and [#982] by [@jneem].

While still incomplete this lays the foundation for running druid on Linux without relying on GTK.

#### Web backend for druid-shell.

[@elrnv] continued the work of [@tedsta] and implemented a mostly complete web backend
via WebAssembly (Wasm) in [#759] and enabled all druid examples to
[run in the browser](https://elrnv.github.io/druid-wasm-examples/).

While some features like the clipboard, menus or file dialogs are not yet available,
all fundamental features are there.

#### Using Core Graphics on macOS.

[@cmyr] continued the work of [@jrmuizel] and implemented Core Graphics support for Piet in
[piet#176](https://github.com/linebender/piet/pull/176).

Those changes made it into druid via [#905].
This means that druid no longer requires cairo on macOS and uses Core Graphics instead.

### Added

- Standardized and exposed more methods on more contexts. ([#970], [#972], [#855] by [@cmyr], [#898] by [@finnerale], [#954] by [@xStrom], [#917] by [@jneem])
- `im` feature, with `Data` support for the [`im` crate](https://docs.rs/im/) collections. ([#924] by [@cmyr])
- `im::Vector` support for the `List` widget. ([#940] by [@xStrom])
- `TextBox` can receive `EditAction` commands. ([#814] by [@cmyr])
- `Split::min_splitter_area(f64)` to add padding around the splitter bar. ([#738] by [@xStrom])
- Published `druid::text` module. ([#816] by [@cmyr])
- `InternalEvent::MouseLeave` signalling the cursor left the window. ([#821] by [@teddemunnik])
- `InternalEvent::RouteTimer` to route timer events. ([#831] by [@sjoshid])
- `children_changed` now always includes layout and paint request. ([#839] by [@xStrom])
- `request_paint_rect` for partial invalidation. ([#817] by [@jneem])
- Window title can be any `LabelText` (such as a simple `String`). ([#869] by [@cmyr])
- `Label::with_font` and `set_font`. ([#785] by [@thecodewarrior])
- `MouseEvent` now has a `focus` field which is `true` with window focusing left clicks on macOS. ([#842] by [@xStrom])
- `MouseButtons` to `MouseEvent` to track which buttons are being held down during an event. ([#843] by [@xStrom])
- `Env` and `Key` gained methods for inspecting an `Env` at runtime ([#880] by [@Zarenor])
- `WinHandler::scale` method to inform of scale changes. ([#904] by [@xStrom])
- `WidgetExt::debug_widget_id`, for displaying widget ids on hover. ([#876] by [@cmyr])
- `LifeCycle::Size` event to inform widgets that their size changed. ([#953] by [@xStrom])
- `FileDialogOptions` methods `default_name`, `name_label`, `title`, `button_text`, `packages_as_directories`, `force_starting_directory`. ([#960] by [@xStrom])
- `Button::dynamic` constructor. ([#963] by [@totsteps])
- `Spinner` widget to represent loading states. ([#1003] by [@futurepaul])
- Link to the widget_nursery in README ([#1754] by [@xarvic])

### Changed

- Renamed `WidgetPod` methods: `paint` to `paint_raw`, `paint_with_offset` to `paint`, `paint_with_offset_always` to `paint_always`. ([#980] by [@totsteps])
- Renamed `Event::MouseMoved` to `MouseMove`. ([#825] by [@teddemunnik])
- Renamed `Split` constructors to `Split::rows` and `columns`. ([#738] by [@xStrom])
- Replaced `NEW_WINDOW`, `SET_MENU` and `SHOW_CONTEXT_MENU` commands with methods on `EventCtx` and `DelegateCtx`. ([#931] by [@finnerale])
- Replaced `Command::one_shot` and `::take_object` with a `SingleUse` payload wrapper type. ([#959] by [@finnerale])
- `Command` and `Selector` have been reworked and are now statically typed, similarly to `Env` and `Key`. ([#993] by [@finnerale])
- `AppDelegate::command` now receives a `Target` instead of a `&Target`. ([#909] by [@xStrom])
- `SHOW_WINDOW` and `CLOSE_WINDOW` commands now only use `Target` to determine the affected window. ([#928] by [@finnerale])
- Global `Application` associated functions are instance methods instead, e.g. `Application::global().quit()` instead of the old `Application::quit()`. ([#763] by [@xStrom])
- `Event::Internal(InternalEvent)` bundles all internal events. ([#833] by [@xStrom])
- Timer events will only be delivered to the widgets that requested them. ([#831] by [@sjoshid])
- `Split::splitter_size` no longer includes padding. ([#738] by [@xStrom])
- `has_focus` no longer returns false positives. ([#819] by [@xStrom])
- `WidgetPod::set_layout_rect` now requires `LayoutCtx`, data and `Env`. ([#841] by [@xStrom])
- `request_timer` uses `Duration` instead of `Instant`. ([#847] by [@finnerale])
- `Event::Wheel` now contains a `MouseEvent` structure. ([#895] by [@teddemunnik])
- The `WindowHandle::get_dpi` method got replaced by `WindowHandle::get_scale`. ([#904] by [@xStrom])
- The `WinHandler::size` method now gets a `Size` in display points. ([#904] by [@xStrom])
- Standardized the type returned by the contexts' `text` methods. ([#996] by [@cmyr])
- `ViewSwitcher` uses `Data` type constraint instead of `PartialEq`. ([#1112] by [@justinmoon])

### Removed

- The optional GTK feature for non-Linux platforms. ([#611] by [@pyroxymat])

### Fixed

- `Event::HotChanged(false)` will be emitted when the cursor leaves the window. ([#821] by [@teddemunnik])
- Keep hot state consistent with mouse position. ([#841] by [@xStrom])
- Start focus cycling from not-registered-for-focus widgets. ([#819] by [@xStrom])
- Supply correct `LifeCycleCtx` to `Event::FocusChanged`. ([#878] by [@cmyr])
- Propagate `Event::FocusChanged` to focus gaining widgets as well. ([#819] by [@xStrom])
- Routing `LifeCycle::FocusChanged` to descendant widgets. ([#925] by [@yrns])
- Focus request handling is now predictable with the last request overriding earlier ones. ([#948] by [@xStrom])
- Open file menu item works again. ([#851] by [@kindlychung])
- Built-in open and save menu items now show the correct label and submit the right commands. ([#930] by [@finnerale])
- Wheel events now properly update hot state. ([#951] by [@xStrom])
- macOS: Support `FileDialogOptions::default_type`. ([#960] by [@xStrom])
- macOS: Show the save dialog even with `FileDialogOptions` `select_directories` and `multi_selection` set. ([#960] by [@xStrom])
- X11: Support mouse scrolling. ([#961] by [@jneem])
- `Painter` now properly repaints on data change in `Container`. ([#991] by [@cmyr])
- Windows: Terminate app when all windows have closed. ([#763] by [@xStrom])
- Windows: Respect the minimum window size. ([#727] by [@teddemunnik])
- Windows: Respect resizability. ([#712] by [@teddemunnik])
- Windows: Capture mouse for drag actions. ([#695] by [@teddemunnik])
- Windows: Removed flashes of white background at the edge of the window when resizing. ([#915] by [@xStrom])
- Windows: Reduced chance of white flash when opening a new window. ([#916] by [@xStrom])
- Windows: Keep receiving mouse events after pressing ALT or F10 when the window has no menu. ([#997] by [@xStrom])
- macOS: `Application::quit` now quits the run loop instead of killing the process. ([#763] by [@xStrom])
- macOS: `Event::HotChanged` is properly generated with multiple windows. ([#907] by [@xStrom])
- macOS: The application menu is now immediately interactable after launch. ([#994] by [@xStrom])
- macOS/GTK: `MouseButton::X1` and `MouseButton::X2` clicks are now recognized. ([#843] by [@xStrom])
- GTK: Use the system locale. ([#798] by [@finnerale])
- GTK: Actually close windows. ([#797] by [@finnerale])
- GTK: Prevent crashing on pop-ups. ([#837] by [@finnerale])
- GTK: Support disabled menu items. ([#897] by [@jneem])
- GTK: Support file filters in open/save dialogs. ([#903] by [@jneem])
- GTK: Support DPI values other than 96. ([#904] by [@xStrom])

### Visual

- Improved `Split` accuracy. ([#738] by [@xStrom])
- Built-in widgets no longer stroke outside their `paint_rect`. ([#861] by [@jneem])
- `Switch` toggles with animation when its data changes externally. ([#898] by [@finnerale])
- Render progress bar correctly. ([#949] by [@scholtzan])
- Scrollbars animate when the scroll container size changes. ([#964] by [@xStrom])

### Docs

- Added example and usage hints to `Env`. ([#796] by [@finnerale])
- Added documentation about the usage of bloom filters. ([#818] by [@xStrom])
- Added book chapters about `Painter` and `Controller`. ([#832] by [@cmyr])
- Added a changelog containing development since the 0.5 release. ([#889] by [@finnerale])
- Added goals section to `README.md`. ([#971] by [@finnerale])
- Added a section about dependencies to `CONTRIBUTING.md`. ([#990] by [@xStrom])
- Updated screenshots in `README.md`. ([#967] by [@xStrom])
- Removed references to cairo on macOS. ([#943] by [@xStrom])

### Examples

- Added `blocking_function`. ([#840] by [@mastfissh])
- Added hot glow option to `multiwin`. ([#845] by [@xStrom])
- Reduce the flashing in `ext_event` and `identity`. ([#782] by [@futurepaul])
- Fixed menu inconsistency across multiple windows in `multiwin`. ([#926] by [@kindlychung])

### Maintenance

- Added rendering tests. ([#784] by [@fishrockz])
- Added docs generation testing for all features. ([#942] by [@xStrom])
- Replaced `#[macro_use]` with normal `use`. ([#808] by [@totsteps])
- Enabled Clippy checks for all targets. ([#850] by [@xStrom])
- Revamped CI testing to optimize coverage and speed. ([#857] by [@xStrom])
- Refactored DPI scaling. ([#904] by [@xStrom])
- Refactored `WidgetPod::event` to improve readability and performance of more complex logic. ([#1001] by [@xStrom])
- Renamed `BaseState` to `WidgetState` ([#969] by [@cmyr])
- Fixed test harness crashing on failure. ([#984] by [@xStrom])
- GTK: Refactored `Application` to use the new structure. ([#892] by [@xStrom])

### Outside News

- There are new projects using druid:
  - [Kondo](https://github.com/tbillington/kondo) Save disk space by cleaning unneeded files from software projects.
  - [jack-mixer](https://github.com/derekdreery/jack-mixer) A jack client that provides mixing, levels and a 3-band eq.
  - [kiro-synth](https://github.com/chris-zen/kiro-synth) An in progress modular sound synthesizer.

## [0.5.0] - 2020-04-01

Last release without a changelog :(

## [0.4.0] - 2019-12-28
## [0.3.2] - 2019-11-05
## [0.3.1] - 2019-11-04
## 0.3.0 - 2019-11-02
## 0.1.1 - 2018-11-02
## 0.1.0 - 2018-11-02

[@arthmis]: https://github.com/arthmis
[@futurepaul]: https://github.com/futurepaul
[@finnerale]: https://github.com/finnerale
[@totsteps]: https://github.com/totsteps
[@cmyr]: https://github.com/cmyr
[@xStrom]: https://github.com/xStrom
[@teddemunnik]: https://github.com/teddemunnik
[@crsaracco]: https://github.com/crsaracco
[@pyroxymat]: https://github.com/pyroxymat
[@elrnv]: https://github.com/elrnv
[@tedsta]: https://github.com/tedsta
[@kindlychung]: https://github.com/kindlychung
[@jneem]: https://github.com/jneem
[@fishrockz]: https://github.com/fishrockz
[@thecodewarrior]: https://github.com/thecodewarrior
[@sjoshid]: https://github.com/sjoshid
[@mastfissh]: https://github.com/mastfissh
[@Zarenor]: https://github.com/Zarenor
[@yrns]: https://github.com/yrns
[@jrmuizel]: https://github.com/jrmuizel
[@scholtzan]: https://github.com/scholtzan
[@covercash2]: https://github.com/covercash2
[@raphlinus]: https://github.com/raphlinus
[@binomial0]: https://github.com/binomial0
[@ForLoveOfCats]: https://github.com/ForLoveOfCats
[@chris-zen]: https://github.com/chris-zen
[@vkahl]: https://github.com/vkahl
[@psychon]: https://github.com/psychon
[@sysint64]: https://github.com/sysint64
[@justinmoon]: https://github.com/justinmoon
[@rjwittams]: https://github.com/rjwittams
[@rhzk]: https://github.com/rhzk
[@koutoftimer]: https://github.com/koutoftimer
[@tay64]: https://github.com/tay64
[@JAicewizard]: https://github.com/JAicewizard
[@andrewhickman]: https://github.com/andrewhickman
[@colinfruit]: https://github.com/colinfruit
[@Maan2003]: https://github.com/Maan2003
[@derekdreery]: https://github.com/derekdreery
[@MaximilianKoestler]: https://github.com/MaximilianKoestler
[@lassipulkkinen]: https://github.com/lassipulkkinen
[@Poignardazur]: https://github.com/PoignardAzur
[@HoNile]: https://github.com/HoNile
[@SecondFlight]: https://github.com/SecondFlight
[@lord]: https://github.com/lord
[@Lejero]: https://github.com/Lejero
[@lidin]: https://github.com/lidin
[@xarvic]: https://github.com/xarvic
[@arthmis]: https://github.com/arthmis
[@ccqpein]: https://github.com/ccqpein
[@RichardPoole42]: https://github.com/RichardPoole42
[@r-ml]: https://github.com/r-ml
[@djeedai]: https://github.com/djeedai
[@bjorn]: https://github.com/bjorn
[@DrGabble]: https://github.com/DrGabble
[@lisael]: https://github.com/lisael
[@jenra-uwu]: https://github.com/jenra-uwu
[@klemensn]: https://github.com/klemensn
[@agentsim]: https://github.com/agentsim
[@jplatte]: https://github.com/jplatte
[@zedseven]: https://github.com/zedseven
[@Pavel-N]: https://github.com/Pavel-N
[@maurerdietmar]: https://github.com/maurerdietmar
[@superfell]: https://github.com/superfell
[@GoldsteinE]: https://github.com/GoldsteinE
[@twitchyliquid64]: https://github.com/twitchyliquid64
[@dristic]: https://github.com/dristic
[@NickLarsenNZ]: https://github.com/NickLarsenNZ
[@barsae]: https://github.com/barsae
[@amtep]: https://github.com/amtep
[@ThomasMcandrew]: https:github.com/ThomasMcandrew
[@benoitryder]: https://github.com/benoitryder
[@sprocklem]: https://github.com/sprocklem
[@cbondurant]: https://github.com/cbondurant

[#599]: https://github.com/linebender/druid/pull/599
[#611]: https://github.com/linebender/druid/pull/611
[#695]: https://github.com/linebender/druid/pull/695
[#712]: https://github.com/linebender/druid/pull/712
[#727]: https://github.com/linebender/druid/pull/727
[#738]: https://github.com/linebender/druid/pull/738
[#759]: https://github.com/linebender/druid/pull/759
[#763]: https://github.com/linebender/druid/pull/763
[#782]: https://github.com/linebender/druid/pull/782
[#784]: https://github.com/linebender/druid/pull/784
[#785]: https://github.com/linebender/druid/pull/785
[#796]: https://github.com/linebender/druid/pull/796
[#797]: https://github.com/linebender/druid/pull/797
[#798]: https://github.com/linebender/druid/pull/798
[#808]: https://github.com/linebender/druid/pull/808
[#814]: https://github.com/linebender/druid/pull/814
[#816]: https://github.com/linebender/druid/pull/816
[#817]: https://github.com/linebender/druid/pull/817
[#818]: https://github.com/linebender/druid/pull/818
[#819]: https://github.com/linebender/druid/pull/819
[#821]: https://github.com/linebender/druid/pull/821
[#825]: https://github.com/linebender/druid/pull/825
[#831]: https://github.com/linebender/druid/pull/831
[#832]: https://github.com/linebender/druid/pull/832
[#833]: https://github.com/linebender/druid/pull/833
[#837]: https://github.com/linebender/druid/pull/837
[#839]: https://github.com/linebender/druid/pull/839
[#840]: https://github.com/linebender/druid/pull/840
[#841]: https://github.com/linebender/druid/pull/841
[#842]: https://github.com/linebender/druid/pull/842
[#843]: https://github.com/linebender/druid/pull/843
[#845]: https://github.com/linebender/druid/pull/845
[#847]: https://github.com/linebender/druid/pull/847
[#850]: https://github.com/linebender/druid/pull/850
[#851]: https://github.com/linebender/druid/pull/851
[#855]: https://github.com/linebender/druid/pull/855
[#857]: https://github.com/linebender/druid/pull/857
[#861]: https://github.com/linebender/druid/pull/861
[#869]: https://github.com/linebender/druid/pull/869
[#876]: https://github.com/linebender/druid/pull/876
[#878]: https://github.com/linebender/druid/pull/878
[#880]: https://github.com/linebender/druid/pull/880
[#889]: https://github.com/linebender/druid/pull/889
[#892]: https://github.com/linebender/druid/pull/892
[#894]: https://github.com/linebender/druid/pull/894
[#895]: https://github.com/linebender/druid/pull/895
[#897]: https://github.com/linebender/druid/pull/897
[#898]: https://github.com/linebender/druid/pull/898
[#900]: https://github.com/linebender/druid/pull/900
[#903]: https://github.com/linebender/druid/pull/903
[#904]: https://github.com/linebender/druid/pull/904
[#905]: https://github.com/linebender/druid/pull/905
[#907]: https://github.com/linebender/druid/pull/907
[#909]: https://github.com/linebender/druid/pull/909
[#913]: https://github.com/linebender/druid/pull/913
[#915]: https://github.com/linebender/druid/pull/915
[#916]: https://github.com/linebender/druid/pull/916
[#917]: https://github.com/linebender/druid/pull/917
[#920]: https://github.com/linebender/druid/pull/920
[#924]: https://github.com/linebender/druid/pull/924
[#925]: https://github.com/linebender/druid/pull/925
[#926]: https://github.com/linebender/druid/pull/926
[#928]: https://github.com/linebender/druid/pull/928
[#930]: https://github.com/linebender/druid/pull/930
[#931]: https://github.com/linebender/druid/pull/931
[#940]: https://github.com/linebender/druid/pull/940
[#942]: https://github.com/linebender/druid/pull/942
[#943]: https://github.com/linebender/druid/pull/943
[#948]: https://github.com/linebender/druid/pull/948
[#949]: https://github.com/linebender/druid/pull/949
[#951]: https://github.com/linebender/druid/pull/951
[#953]: https://github.com/linebender/druid/pull/953
[#954]: https://github.com/linebender/druid/pull/954
[#957]: https://github.com/linebender/druid/pull/957
[#959]: https://github.com/linebender/druid/pull/959
[#960]: https://github.com/linebender/druid/pull/960
[#961]: https://github.com/linebender/druid/pull/961
[#963]: https://github.com/linebender/druid/pull/963
[#964]: https://github.com/linebender/druid/pull/964
[#967]: https://github.com/linebender/druid/pull/967
[#969]: https://github.com/linebender/druid/pull/969
[#970]: https://github.com/linebender/druid/pull/970
[#971]: https://github.com/linebender/druid/pull/971
[#972]: https://github.com/linebender/druid/pull/972
[#980]: https://github.com/linebender/druid/pull/980
[#982]: https://github.com/linebender/druid/pull/982
[#984]: https://github.com/linebender/druid/pull/984
[#990]: https://github.com/linebender/druid/pull/990
[#991]: https://github.com/linebender/druid/pull/991
[#993]: https://github.com/linebender/druid/pull/993
[#994]: https://github.com/linebender/druid/pull/994
[#996]: https://github.com/linebender/druid/pull/996
[#997]: https://github.com/linebender/druid/pull/997
[#1001]: https://github.com/linebender/druid/pull/1001
[#1003]: https://github.com/linebender/druid/pull/1003
[#1007]: https://github.com/linebender/druid/pull/1007
[#1008]: https://github.com/linebender/druid/pull/1008
[#1011]: https://github.com/linebender/druid/pull/1011
[#1013]: https://github.com/linebender/druid/pull/1013
[#1018]: https://github.com/linebender/druid/pull/1018
[#1025]: https://github.com/linebender/druid/pull/1025
[#1028]: https://github.com/linebender/druid/pull/1028
[#1037]: https://github.com/linebender/druid/pull/1037
[#1042]: https://github.com/linebender/druid/pull/1042
[#1043]: https://github.com/linebender/druid/pull/1043
[#1049]: https://github.com/linebender/druid/pull/1049
[#1050]: https://github.com/linebender/druid/pull/1050
[#1054]: https://github.com/linebender/druid/pull/1054
[#1057]: https://github.com/linebender/druid/pull/1057
[#1058]: https://github.com/linebender/druid/pull/1058
[#1061]: https://github.com/linebender/druid/pull/1061
[#1062]: https://github.com/linebender/druid/pull/1062
[#1072]: https://github.com/linebender/druid/pull/1072
[#1075]: https://github.com/linebender/druid/pull/1075
[#1076]: https://github.com/linebender/druid/pull/1076
[#1081]: https://github.com/linebender/druid/pull/1081
[#1091]: https://github.com/linebender/druid/pull/1091
[#1096]: https://github.com/linebender/druid/pull/1096
[#1097]: https://github.com/linebender/druid/pull/1097
[#1093]: https://github.com/linebender/druid/pull/1093
[#1100]: https://github.com/linebender/druid/pull/1100
[#1103]: https://github.com/linebender/druid/pull/1103
[#1107]: https://github.com/linebender/druid/pull/1107
[#1118]: https://github.com/linebender/druid/pull/1118
[#1119]: https://github.com/linebender/druid/pull/1119
[#1120]: https://github.com/linebender/druid/pull/1120
[#1126]: https://github.com/linebender/druid/pull/1120
[#1128]: https://github.com/linebender/druid/pull/1128
[#1133]: https://github.com/linebender/druid/pull/1133
[#1143]: https://github.com/linebender/druid/pull/1143
[#1145]: https://github.com/linebender/druid/pull/1145
[#1151]: https://github.com/linebender/druid/pull/1151
[#1152]: https://github.com/linebender/druid/pull/1152
[#1155]: https://github.com/linebender/druid/pull/1155
[#1157]: https://github.com/linebender/druid/pull/1157
[#1160]: https://github.com/linebender/druid/pull/1160
[#1171]: https://github.com/linebender/druid/pull/1171
[#1172]: https://github.com/linebender/druid/pull/1172
[#1173]: https://github.com/linebender/druid/pull/1173
[#1182]: https://github.com/linebender/druid/pull/1182
[#1183]: https://github.com/linebender/druid/pull/1183
[#1185]: https://github.com/linebender/druid/pull/1185
[#1191]: https://github.com/linebender/druid/pull/1191
[#1092]: https://github.com/linebender/druid/pull/1092
[#1189]: https://github.com/linebender/druid/pull/1189
[#1195]: https://github.com/linebender/druid/pull/1195
[#1204]: https://github.com/linebender/druid/pull/1204
[#1205]: https://github.com/linebender/druid/pull/1205
[#1207]: https://github.com/linebender/druid/pull/1207
[#1210]: https://github.com/linebender/druid/pull/1210
[#1214]: https://github.com/linebender/druid/pull/1214
[#1226]: https://github.com/linebender/druid/pull/1226
[#1232]: https://github.com/linebender/druid/pull/1232
[#1231]: https://github.com/linebender/druid/pull/1231
[#1220]: https://github.com/linebender/druid/pull/1220
[#1238]: https://github.com/linebender/druid/pull/1238
[#1241]: https://github.com/linebender/druid/pull/1241
[#1245]: https://github.com/linebender/druid/pull/1245
[#1248]: https://github.com/linebender/druid/pull/1248
[#1251]: https://github.com/linebender/druid/pull/1251
[#1252]: https://github.com/linebender/druid/pull/1252
[#1255]: https://github.com/linebender/druid/pull/1255
[#1272]: https://github.com/linebender/druid/pull/1272
[#1276]: https://github.com/linebender/druid/pull/1276
[#1278]: https://github.com/linebender/druid/pull/1278
[#1280]: https://github.com/linebender/druid/pull/1280
[#1283]: https://github.com/linebender/druid/pull/1283
[#1295]: https://github.com/linebender/druid/pull/1280
[#1298]: https://github.com/linebender/druid/pull/1298
[#1299]: https://github.com/linebender/druid/pull/1299
[#1302]: https://github.com/linebender/druid/pull/1302
[#1306]: https://github.com/linebender/druid/pull/1306
[#1311]: https://github.com/linebender/druid/pull/1311
[#1320]: https://github.com/linebender/druid/pull/1320
[#1324]: https://github.com/linebender/druid/pull/1324
[#1326]: https://github.com/linebender/druid/pull/1326
[#1328]: https://github.com/linebender/druid/pull/1328
[#1346]: https://github.com/linebender/druid/pull/1346
[#1351]: https://github.com/linebender/druid/pull/1351
[#1259]: https://github.com/linebender/druid/pull/1259
[#1361]: https://github.com/linebender/druid/pull/1361
[#1371]: https://github.com/linebender/druid/pull/1371
[#1401]: https://github.com/linebender/druid/pull/1401
[#1410]: https://github.com/linebender/druid/pull/1410
[#1423]: https://github.com/linebender/druid/pull/1423
[#1433]: https://github.com/linebender/druid/pull/1433
[#1438]: https://github.com/linebender/druid/pull/1438
[#1441]: https://github.com/linebender/druid/pull/1441
[#1448]: https://github.com/linebender/druid/pull/1448
[#1463]: https://github.com/linebender/druid/pull/1463
[#1452]: https://github.com/linebender/druid/pull/1452
[#1485]: https://github.com/linebender/druid/pull/1485
[#1520]: https://github.com/linebender/druid/pull/1520
[#1523]: https://github.com/linebender/druid/pull/1523
[#1526]: https://github.com/linebender/druid/pull/1526
[#1532]: https://github.com/linebender/druid/pull/1532
[#1533]: https://github.com/linebender/druid/pull/1533
[#1534]: https://github.com/linebender/druid/pull/1534
[#1254]: https://github.com/linebender/druid/pull/1254
[#1559]: https://github.com/linebender/druid/pull/1559
[#1561]: https://github.com/linebender/druid/pull/1561
[#1562]: https://github.com/linebender/druid/pull/1562
[#1592]: https://github.com/linebender/druid/pull/1592
[#1596]: https://github.com/linebender/druid/pull/1596
[#1600]: https://github.com/linebender/druid/pull/1600
[#1606]: https://github.com/linebender/druid/pull/1606
[#1619]: https://github.com/linebender/druid/pull/1619
[#1625]: https://github.com/linebender/druid/pull/1625
[#1632]: https://github.com/linebender/druid/pull/1632
[#1634]: https://github.com/linebender/druid/pull/1634
[#1635]: https://github.com/linebender/druid/pull/1635
[#1636]: https://github.com/linebender/druid/pull/1636
[#1640]: https://github.com/linebender/druid/pull/1640
[#1641]: https://github.com/linebender/druid/pull/1641
[#1645]: https://github.com/linebender/druid/pull/1645
[#1647]: https://github.com/linebender/druid/pull/1647
[#1654]: https://github.com/linebender/druid/pull/1654
[#1660]: https://github.com/linebender/druid/pull/1660
[#1662]: https://github.com/linebender/druid/pull/1662
[#1677]: https://github.com/linebender/druid/pull/1677
[#1691]: https://github.com/linebender/druid/pull/1691
[#1693]: https://github.com/linebender/druid/pull/1693
[#1695]: https://github.com/linebender/druid/pull/1695
[#1696]: https://github.com/linebender/druid/pull/1696
[#1698]: https://github.com/linebender/druid/pull/1698
[#1702]: https://github.com/linebender/druid/pull/1702
[#1713]: https://github.com/linebender/druid/pull/1713
[#1715]: https://github.com/linebender/druid/pull/1715
[#1717]: https://github.com/linebender/druid/pull/1717
[#1722]: https://github.com/linebender/druid/pull/1722
[#1724]: https://github.com/linebender/druid/pull/1724
[#1730]: https://github.com/linebender/druid/pull/1730
[#1737]: https://github.com/linebender/druid/pull/1737
[#1743]: https://github.com/linebender/druid/pull/1743
[#1746]: https://github.com/linebender/druid/pull/1746
[#1751]: https://github.com/linebender/druid/pull/1751
[#1754]: https://github.com/linebender/druid/pull/1754
[#1755]: https://github.com/linebender/druid/pull/1755
[#1756]: https://github.com/linebender/druid/pull/1756
[#1761]: https://github.com/linebender/druid/pull/1761
[#1764]: https://github.com/linebender/druid/pull/1764
[#1772]: https://github.com/linebender/druid/pull/1772
[#1779]: https://github.com/linebender/druid/pull/1779
[#1787]: https://github.com/linebender/druid/pull/1787
[#1801]: https://github.com/linebender/druid/pull/1801
[#1802]: https://github.com/linebender/druid/pull/1802
[#1803]: https://github.com/linebender/druid/pull/1803
[#1804]: https://github.com/linebender/druid/pull/1804
[#1805]: https://github.com/linebender/druid/pull/1805
[#1820]: https://github.com/linebender/druid/pull/1820
[#1825]: https://github.com/linebender/druid/pull/1825
[#1828]: https://github.com/linebender/druid/pull/1828
[#1843]: https://github.com/linebender/druid/pull/1843
[#1850]: https://github.com/linebender/druid/pull/1850
[#1851]: https://github.com/linebender/druid/pull/1851
[#1860]: https://github.com/linebender/druid/pull/1860
[#1861]: https://github.com/linebender/druid/pull/1861
[#1863]: https://github.com/linebender/druid/pull/1863
[#1865]: https://github.com/linebender/druid/pull/1865
[#1866]: https://github.com/linebender/druid/pull/1866
[#1867]: https://github.com/linebender/druid/pull/1867
[#1868]: https://github.com/linebender/druid/pull/1868
[#1873]: https://github.com/linebender/druid/pull/1873
[#1876]: https://github.com/linebender/druid/pull/1876
[#1882]: https://github.com/linebender/druid/pull/1882
[#1884]: https://github.com/linebender/druid/pull/1884
[#1885]: https://github.com/linebender/druid/pull/1885
[#1886]: https://github.com/linebender/druid/pull/1886
[#1907]: https://github.com/linebender/druid/pull/1907
[#1919]: https://github.com/linebender/druid/pull/1919
[#1929]: https://github.com/linebender/druid/pull/1929
[#1938]: https://github.com/linebender/druid/pull/1938
[#1947]: https://github.com/linebender/druid/pull/1947
[#1953]: https://github.com/linebender/druid/pull/1953
[#1967]: https://github.com/linebender/druid/pull/1967
[#1976]: https://github.com/linebender/druid/pull/1976
[#1978]: https://github.com/linebender/druid/pull/1978
[#1993]: https://github.com/linebender/druid/pull/1993
[#1996]: https://github.com/linebender/druid/pull/1996
[#2036]: https://github.com/linebender/druid/pull/2036
[#2064]: https://github.com/linebender/druid/pull/2064
[#1979]: https://github.com/linebender/druid/pull/1979
[#2119]: https://github.com/linebender/druid/pull/2119
[#2111]: https://github.com/linebender/druid/pull/2111
[#2117]: https://github.com/linebender/druid/pull/2117
[#2117]: https://github.com/linebender/druid/pull/2141
[#2145]: https://github.com/linebender/druid/pull/2145
[#2148]: https://github.com/linebender/druid/pull/2148
[#2149]: https://github.com/linebender/druid/pull/2149
[#2151]: https://github.com/linebender/druid/pull/2151
[#2157]: https://github.com/linebender/druid/pull/2157
[#2158]: https://github.com/linebender/druid/pull/2158
[#2172]: https://github.com/linebender/druid/pull/2172
[#2195]: https://github.com/linebender/druid/pull/2195
[#2196]: https://github.com/linebender/druid/pull/2196
[#2203]: https://github.com/linebender/druid/pull/2203
[#2235]: https://github.com/linebender/druid/pull/2235
[#2247]: https://github.com/linebender/druid/pull/2247
[#2274]: https://github.com/linebender/druid/pull/2274
[#2284]: https://github.com/linebender/druid/pull/2284
[#2319]: https://github.com/linebender/druid/pull/2319
[#2320]: https://github.com/linebender/druid/pull/2320
[#2323]: https://github.com/linebender/druid/pull/2323
[#2324]: https://github.com/linebender/druid/pull/2324
[#2331]: https://github.com/linebender/druid/pull/2331

[Unreleased]: https://github.com/linebender/druid/compare/v0.7.0...master
[0.7.0]: https://github.com/linebender/druid/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/linebender/druid/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/linebender/druid/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/linebender/druid/compare/v0.3.2...v0.4.0
[0.3.2]: https://github.com/linebender/druid/compare/v0.3.1...v0.3.2
[0.3.1]: https://github.com/linebender/druid/compare/v0.3.0...v0.3.1

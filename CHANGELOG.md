# Change Log

All notable changes to this project will be documented in this file. This
project adheres to [Semantic Versioning](http://semver.org).

## [Unreleased]

Nothing at the moment.

[Unreleased]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.7...HEAD

## [5.0.0-beta.7] - 2016-11-03

### Added

- Added `white-space: nowrap;` to the `hide-visually` mixin so that content
  renders on one line and is correctly pronounced by screen readers. You can
  read more about this in Jesse Beach’s article “[Beware smushed off-screen
    accessible text][smushed-text-article].”

### Changed

- Removed the default values from the `$position` and `$coordinates` arguments
  for the `position` mixin.
- Updated `contrast-switch` to calculate contrast based on the WCAG 2.0
  specification. Please note that it is an approximation and we cannot guarantee
  full compliance, though all of our manual testing passed.
- Renamed the `$coordinates` argument in the `position` mixin
  to `$box-edge-values`.
- Updated `$font-stack-system` to include Avenir Next, Avenir, Lucida
  Grande, Helvetica, Noto, Franklin Gothic Medium, Century Gothic, and
  Liberation Sans. This follows [system-fonts] by Adam Morse.
- The `word-break` property was removed from the `word-wrap` mixin and
  is no longer output.
- Renamed the `word-wrap` mixin to `overflow-wrap` to align with the
  name change in the [CSS spec].

[smushed-text-article]: https://medium.com/@jessebeach/beware-smushed-off-screen-accessible-text-5952a4c2cbfe#.l4hkljiza
[system-fonts]: https://github.com/mrmrs/css-system-fonts
[CSS spec]: https://drafts.csswg.org/css-text-3/#propdef-overflow-wrap

[5.0.0-beta.7]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.6...v5.0.0.beta.7

## [5.0.0-beta.6] - 2016-06-06

### Added

- Added a `value-prefixer` mixin for generating vendor prefixes on values.

[5.0.0-beta.6]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.5...v5.0.0.beta.6

## [5.0.0-beta.5] - 2016-03-23

### Fixed

- Fixed a Sass load path issue that would intermittently break the importing of
  Bourbon in Rails apps.

### Changed

- Swapped the order of the `$file-formats` and `$asset-pipeline` arguments in
  the `font-face` mixin, so that `$asset-pipeline` is last (because it has a
  default and is likely used the least).

[5.0.0-beta.5]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.4...v5.0.0.beta.5

## [5.0.0-beta.4] - 2016-03-11

### Fixed

- We accidentally published `5.0.0.beta.3` as a stable release on npm, rather
  than a prerelease. We’ve unpublished that to go back to `4.2.6` on the stable
  channel.

[5.0.0-beta.4]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.3...v5.0.0.beta.4

## [5.0.0-beta.3] - 2016-03-04

### Fixed

- Added `pathname` requirement to fix install issues.

[5.0.0-beta.3]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.2...v5.0.0.beta.3

## [5.0.0-beta.2] - 2016-03-03

### Added

- Added global settings for the `contrast-switch` mixin:
  `contrast-switch-dark-color` & `contrast-switch-light-color`.
- Added the `triangle` mixin back, but note that it’s been refactored and the
  arguments have changed. See [43e5a90].

### Changed

- Switched argument names in `contrast-switch`; `$dark-color` is now
  `$light-color` and `$light-color` is now `$dark-color`.
- The `is-light` function is now private.

### Removed

- Dropped support for Ruby on Rails versions older than 4.2.
- Dropped support for LibSass versions older than 3.3.

[5.0.0-beta.2]: https://github.com/thoughtbot/bourbon/compare/v5.0.0.beta.1...v5.0.0.beta.2
[43e5a90]: https://github.com/thoughtbot/bourbon/commit/43e5a90e7e624d2977731030ccdb36b3c2e460d9

## [5.0.0-beta.1] - 2016-02-09

### Added

- Added a `contrast-switch` function that switches between two colors based on the
  lightness of a another color. Great for building button styles.
- Added an `$all-text-inputs-invalid` variable to target the `:invalid`
  pseudo-class on all text-based inputs.
- The `ellipsis` mixin now takes a `$display` argument.
- Added a font stack for system fonts: `$font-stack-system`.
- Added a `hide-visually` mixin that hides an element visually while still
  allowing the content to be accessible to assistive technology,
  e.g. screen readers.
- The `font-face` mixin now allows additional CSS properties to be included in
  its block, which will output as part of the `@font-face` declaration.
  See [2356719].

### Changed

- The global default for the `modular-scale` ratio is now set to
  `$major-third` (`1.25`), instead of `$perfect-fourth` (`1.333`).
- All font stack variables are now prefixed with `$font-stack-`,
  e.g. `$font-stack-helvetica`.
- Global settings are now set via a `$bourbon` map, instead of variables.
  See [4e43c2d].
- The `clearfix` mixin now uses `block` display, instead of `table`.

### Removed

- The `$weight` and `$style` arguments in the `font-face` mixin have been
  removed. Instead, you can now include these—along with other CSS
  properties—within the mixin block and they’ll be output as part of the
  `@font-face` declaration.

[5.0.0-beta.1]: https://github.com/thoughtbot/bourbon/compare/da4451e...v5.0.0.beta.1
[2356719]: https://github.com/thoughtbot/bourbon/commit/235671948ef3a9c343c4391d250082a0373c8d83
[4e43c2d]: https://github.com/thoughtbot/bourbon/commit/4e43c2d7507999b539771bdc1b3733b18b3c1883

## [5.0.0.alpha.0] - 2015-08-21

### Added

- Added a `$global-font-file-formats` setting to globally set the file formats
  for the `font-face` mixin. The default is `("ttf", "woff2", "woff")`.
- Add `$consolas`, `$courier-new` and `$monaco` variables (these replace the
  removed `$monospace` variable).

### Changed

- Removed the type selectors in `$all-text-inputs` and `$all-buttons` to
  reduce specificity.
- Font stacks have been modernized. See [3cf106a].
- The `strip-units` function is now `strip-unit`.
- The `size` mixin now requires a comma-separated argument list,
  e.g. `@include size(1em, 2em);`.

### Removed

- All vendor prefixing mixins have been removed. These include:
  - `align-items`
  - `animation-delay`
  - `animation-direction`
  - `animation-duration`
  - `animation-fill-mode`
  - `animation-iteration-count`
  - `animation-name`
  - `animation-play-state`
  - `animation-timing-function`
  - `animation`
  - `appearance`
  - `backface-visibility`
  - `background-image`
  - `background`
  - `border-image`
  - `calc`
  - `column-count`
  - `column-fill`
  - `column-gap`
  - `column-rule-color`
  - `column-rule-style`
  - `column-rule-width`
  - `column-rule`
  - `column-span`
  - `column-width`
  - `columns`
  - `display`
  - `filter`
  - `flex-direction`
  - `flex`
  - `font-feature-settings`
  - `hidpi`
  - `hyphens`
  - `image-rendering`
  - `justify-content`
  - `keyframes`
  - `linear-gradient`
  - `perspective`
  - `placeholder`
  - `radial-gradient`
  - `selection`
  - `text-decoration-color`
  - `text-decoration-line`
  - `text-decoration-style`
  - `text-decoration`
  - `transform-origin`
  - `transform-style`
  - `transform`
  - `transition-delay`
  - `transition-duration`
  - `transition-property`
  - `transition-timing-function`
  - `transition`
  - `user-select`
  - For prefixing, we recommend using a more robust and maintainable solution
    like [Autoprefixer].
- The `$global-prefixes` setting has been removed and the `prefixer` mixin
  has been refactored and no longer uses it.
- The `$monospace` variable has been removed.
- The `box-sizing` mixin has been removed.
- The `button` mixin has been removed.
- The `em` and `rem` mixins have been removed.
- The `flex-grid` function has been removed.
- The `flex-gutter` function has been removed.
- The `golden-ratio` function has been removed.
- The `grid-width` function has been removed.
- The `inline-block` mixin has been removed.
- The `retina-image` mixin has been removed.
- The `triangle` mixin has been removed.

[5.0.0.alpha.0]: https://github.com/thoughtbot/bourbon/compare/v4.2.6...v5.0.0.alpha.0
[3cf106a]: https://github.com/thoughtbot/bourbon/commit/3cf106a210c1bae7765e6193f62310f95fdee0b7
[Autoprefixer]: https://github.com/postcss/autoprefixer
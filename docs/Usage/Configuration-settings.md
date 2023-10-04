# Configuration settings
<!-- This file is auto generated from the source of QROptionsTrait.php -->
## version

QR Code version number

`1 ... 40` or `Version::AUTO` (default)

**See also:**

- `\chillerlan\QRCode\Common\Version`


## versionMin

Minimum QR version

if `QROptions::$version` is set to `Version::AUTO` (default: 1)


## versionMax

Maximum QR version

if `QROptions::$version` is set to `Version::AUTO` (default: 40)


## eccLevel

Error correct level

`EccLevel::X` where `X` is:

- `L` =>  7% (default)
- `M` => 15%
- `Q` => 25%
- `H` => 30%

**See also:**

- `\chillerlan\QRCode\Common\EccLevel`
- [github.com/chillerlan/php-qrcode/discussions/160](https://github.com/chillerlan/php-qrcode/discussions/160)


## maskPattern

Mask Pattern to use (no value in using, mostly for unit testing purposes)

`0 ... 7` or `MaskPattern::PATTERN_AUTO` (default)

**See also:**

- `\chillerlan\QRCode\Common\MaskPattern`


## addQuietzone

Add a "quiet zone" (margin) according to the QR code spec

**See also:**

- [www.qrcode.com/en/howto/code.html](https://www.qrcode.com/en/howto/code.html)


## quietzoneSize

Size of the quiet zone

internally clamped to `0 ... $moduleCount / 2` (default: 4)


## outputType

The built-in output type

- `QROutputInterface::MARKUP_SVG` (default)
- `QROutputInterface::MARKUP_HTML`
- `QROutputInterface::GDIMAGE_BMP`
- `QROutputInterface::GDIMAGE_GIF`
- `QROutputInterface::GDIMAGE_JPG`
- `QROutputInterface::GDIMAGE_PNG`
- `QROutputInterface::GDIMAGE_WEBP`
- `QROutputInterface::STRING_TEXT`
- `QROutputInterface::STRING_JSON`
- `QROutputInterface::IMAGICK`
- `QROutputInterface::EPS`
- `QROutputInterface::FPDF`
- `QROutputInterface::CUSTOM`

**See also:**

- `\chillerlan\QRCode\Output\QREps`
- `\chillerlan\QRCode\Output\QRFpdf`
- `\chillerlan\QRCode\Output\QRGdImage`
- `\chillerlan\QRCode\Output\QRImagick`
- `\chillerlan\QRCode\Output\QRMarkupHTML`
- `\chillerlan\QRCode\Output\QRMarkupSVG`
- `\chillerlan\QRCode\Output\QRString`


## outputInterface

The FQCN of the custom `QROutputInterface`

if `QROptions::$outputType` is set to `QROutputInterface::CUSTOM` (default: `null`)


## returnResource

Return the image resource instead of a render if applicable.

- `QRGdImage`: `resource` (PHP < 8), `GdImage`
- `QRImagick`: `Imagick`
- `QRFpdf`:    `FPDF`

This option overrides/ignores other output settings, such as `QROptions::$cachefile`
and `QROptions::$outputBase64`. (default: `false`)

**See also:**

- `\chillerlan\QRCode\Output\QROutputInterface::dump()`


## cachefile

Optional cache file path `/path/to/cache.file`

Please note that the `$file` parameter in `QRCode::render()` and `QRCode::renderMatrix()`
takes precedence over the `QROptions::$cachefile` value. (default: `null`)

**See also:**

- `\chillerlan\QRCode\QRCode::render()`
- `\chillerlan\QRCode\QRCode::renderMatrix()`


## outputBase64

Toggle base64 data URI or raw data output (if applicable)

(default: `true`)

**See also:**

- `\chillerlan\QRCode\Output\QROutputAbstract::toBase64DataURI()`


## eol

Newline string

(default: `PHP_EOL`)


## bgColor

Sets the image background color (if applicable)

- `QRImagick`: defaults to `"white"`
- `QRGdImage`: defaults to `[255, 255, 255]`
- `QRFpdf`: defaults to blank internally (white page)



## invertMatrix

Whether to invert the matrix (reflectance reversal)

(default: `false`)

**See also:**

- `\chillerlan\QRCode\Data\QRMatrix::invert()`


## drawLightModules

Whether to draw the light (false) modules

(default: `true`)


## drawCircularModules

Specify whether to draw the modules as filled circles

a note for `GdImage` output:

if `QROptions::$scale` is less than 20, the image will be upscaled internally, then the modules will be drawn
using `imagefilledellipse()` and then scaled back to the expected size

No effect in: `QREps`, `QRFpdf`, `QRMarkupHTML`

**See also:**

- [php.net: `\imagefilledellipse()`](https://www.php.net/manual/function.imagefilledellipse)
- [github.com/chillerlan/php-qrcode/issues/23](https://github.com/chillerlan/php-qrcode/issues/23)
- [github.com/chillerlan/php-qrcode/discussions/122](https://github.com/chillerlan/php-qrcode/discussions/122)


## circleRadius

Specifies the radius of the modules when `QROptions::$drawCircularModules` is set to `true`

(default: 0.45)


## keepAsSquare

Specifies which module types to exclude when `QROptions::$drawCircularModules` is set to `true`

(default: `[]`)


## connectPaths

Whether to connect the paths for the several module types to avoid weird glitches when using gradients etc.

**See also:**

- [github.com/chillerlan/php-qrcode/issues/57](https://github.com/chillerlan/php-qrcode/issues/57)


## excludeFromConnect

Specify which paths/patterns to exclude from connecting if `QROptions::$connectPaths` is set to `true`


## moduleValues

Module values map

- `QRImagick`, `QRMarkupHTML`, `QRMarkupSVG`: #ABCDEF, cssname, rgb(), rgba()...
- `QREps`, `QRFpdf`, `QRGdImage`: `[R, G, B]` // 0-255
- `QREps`: `[C, M, Y, K]` // 0-255

**See also:**

- `\chillerlan\QRCode\Output\QROutputAbstract::setModuleValues()`


## addLogoSpace

Toggles logo space creation

**See also:**

- `\chillerlan\QRCode\QRCode::addMatrixModifications()`
- `\chillerlan\QRCode\Data\QRMatrix::setLogoSpace()`


## logoSpaceWidth

Width of the logo space

if only `QROptions::$logoSpaceWidth` is given, the logo space is assumed a square of that size


## logoSpaceHeight

Height of the logo space

if only `QROptions::$logoSpaceHeight` is given, the logo space is assumed a square of that size


## logoSpaceStartX

Optional horizontal start position of the logo space (top left corner)


## logoSpaceStartY

Optional vertical start position of the logo space (top left corner)


## scale

Pixel size of a QR code module


## imageTransparent

Toggle transparency

- `QRGdImage` and `QRImagick`: the given `QROptions::$transparencyColor` is set as transparent

**See also:**

- [github.com/chillerlan/php-qrcode/discussions/121](https://github.com/chillerlan/php-qrcode/discussions/121)


## transparencyColor

Sets a transparency color for when `QROptions::$imageTransparent` is set to `true`.

Defaults to `QROptions::$bgColor`.

- `QRGdImage`: `[R, G, B]`, this color is set as transparent in `imagecolortransparent()`
- `QRImagick`: `"color_str"`, this color is set in `Imagick::transparentPaintImage()`


**See also:**

- [php.net: `\imagecolortransparent()`](https://www.php.net/manual/function.imagecolortransparent)
- [php.net: `\Imagick::transparentPaintImage()`](https://www.php.net/manual/imagick.transparentpaintimage)


## quality

Compression quality

The given value depends on the used output type:

- `QROutputInterface::GDIMAGE_BMP`:  `[0...1]`
- `QROutputInterface::GDIMAGE_JPG`:  `[0...100]`
- `QROutputInterface::GDIMAGE_WEBP`: `[0...9]`
- `QROutputInterface::GDIMAGE_PNG`:  `[0...100]`
- `QROutputInterface::IMAGICK`:      `[0...100]`

**See also:**

- [php.net: `\imagebmp()`](https://www.php.net/manual/function.imagebmp)
- [php.net: `\imagejpeg()`](https://www.php.net/manual/function.imagejpeg)
- [php.net: `\imagepng()`](https://www.php.net/manual/function.imagepng)
- [php.net: `\imagewebp()`](https://www.php.net/manual/function.imagewebp)
- [php.net: `\Imagick::setImageCompressionQuality()`](https://www.php.net/manual/imagick.setimagecompressionquality)


## imagickFormat

Imagick output format

**See also:**

- [php.net: `\Imagick::setImageFormat()`](https://www.php.net/manual/imagick.setimageformat)
- [www.imagemagick.org/script/formats.php](https://www.imagemagick.org/script/formats.php)


## cssClass

A common css class


## markupDark

Markup substitute for dark (CSS value)


## markupLight

Markup substitute for light (CSS value)


## svgAddXmlHeader

Whether to add an XML header line or not, e.g. to embed the SVG directly in HTML

`<?xml version="1.0" encoding="UTF-8"?>`


## svgOpacity

SVG path opacity

Sets the value for the SVG "fill-opacity" on a `<path>` element. Only in effect when non-empty values
for `QROptions::$markupDark` and `QROptions::$markupLight` are given.
The opacity value is the same for all paths - please use CSS for more sophisticated implementations.


## svgDefs

Anything in the SVG `<defs>` tag

**See also:**

- [developer.mozilla.org/en-US/docs/Web/SVG/Element/defs](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/defs)


## svgPreserveAspectRatio

Sets the value for the "preserveAspectRatio" on the `<svg>` element

**See also:**

- [developer.mozilla.org/en-US/docs/Web/SVG/Attribute/preserveAspectRatio](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/preserveAspectRatio)


## textDark

String substitute for dark


## textLight

String substitute for light


## textLineStart

An optional line prefix, e.g. empty space to align the QR Code in a console


## jsonAsBooleans

Whether to return matrix values in JSON as booleans or `$M_TYPE` integers


## fpdfMeasureUnit

Measurement unit for `FPDF` output: pt, mm, cm, in (defaults to "pt")

**See also:**

- `FPDF::__construct()`


## readerUseImagickIfAvailable

Use Imagick (if available) when reading QR Codes


## readerGrayscale

Grayscale the image before reading


## readerIncreaseContrast

Increase the contrast before reading

note that applying contrast works different in GD and Imagick, so mileage may vary

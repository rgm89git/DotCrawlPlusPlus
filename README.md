# <div align="center"><img src="https://user-images.githubusercontent.com/40833244/173114548-6b44afd5-8bd7-4e70-877e-864e99e36803.png" /></div>
#### <p align="center">***A modernization of DotCrawlPlus, an filter that emulates analog artifacts.***</p>

<div align="center">

[![Release version](https://img.shields.io/github/v/release/rgm89git/DotCrawlPlusPlus?color=blue&label=&style=for-the-badge)](https://github.com/rgm89git/DotCrawlPlusPlus/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/rgm89git/DotCrawlPlusPlus/total?style=for-the-badge&color=blue)](https://github.com/rgm89git/DotCrawlPlusPlus/releases/latest)
[![Commits](https://img.shields.io/github/commit-activity/m/rgm89git/DotCrawlPlusPlus?label=commits&style=for-the-badge)](https://github.com/rgm89git/DotCrawlPlusPlus/commits)
[![Last Commit](https://img.shields.io/github/last-commit/rgm89git/DotCrawlPlusPlus/master?label=&style=for-the-badge)](https://github.com/rgm89git/DotCrawlPlusPlus/commits)

</div>

## Demos
**Colorbars w/ Overscan Borders**

<img alt="Colorbars w/ DotCrawl++" src="https://user-images.githubusercontent.com/40833244/173113179-746995d3-2b87-497a-a36f-7cf81ccc8ce6.png" height="320">
  
```avisynth
ColorBars(pixel_type="YV12")
Amplify(0)

Spline64Resize(640,480)
AddBorders(6,0,6,0)
Spline64Resize(640,480)

sharpen(.5)
blur(1)

dcpp_preset("betacam",threads=4)
```

**Test Charts w/ Overscan Borders** *(credits to [belle-nuit.com](https://www.belle-nuit.com/test-chart))*

<img alt="Test Charts w/ Overscan Borders" src="https://user-images.githubusercontent.com/40833244/173119438-d406115a-b9ab-4a8b-99cf-9029392b009a.png" height="320">
  
```
ImageSource("testchartntsc.tif")
ConvertToYV12()

Spline64Resize(640,480)
AddBorders(6,0,6,0)
Spline64Resize(640,480)

sharpen(.5)
blur(1)

dcpp_preset("betacam",threads=4)
```

## Usage

**Choose a preset:**
```
dcpp_preset(clip C, string "preset", float "dots", float "rainbow", bool "showpreset", bool "showargs", float "threads")
@ preset - choices:
           "mild"     - minimal effect
           "medium"   - softer chroma; a little added noise
           "heavy"    - very soft & noisy
           "strong"   - like medium but more so
           "bigdot1"  - larger dots #1
           "bigdot2"  - larger dots #2
           "bigdot3"  - larger dots #3
           "betacam"  - Analog formats - Betacam
           empty string ("") defaults to "medium";
           unrecognized values raise an error.
@ dots     - dotcrawl effect amount
                (default depends on preset)
@ rainbow   - rainbow effect amount
                (default depends on preset)
@ cblur    - chroma blur amount
                (default depends on preset)
@ lblur    - luma blur amount
                (default depends on preset)
@ showpreset - if true, show the preset name as a Subtitle
                (default false)
@ showargs  - if true, show the arguments as a Subtitle
                (default false)
@ threads   - cpu threads you want to use
                (default 4)
```

**Or use the main function *(with your settings)*:**
```
dotcrawlplusplus(clip C, int "dotstyle", float "dotblend", float "dotscale", int "dotleak", int "csub", float "cblur", float "lblur", int "lnoise", int "cnoise", float "streaking", float "rainbow", bool "showargs", float "threads")
@ dotstyle  - dots style (0..2; default 0)
@ dotblend  - dots opacity (default 1.0)
@ dotscale  - scale of dot crawl (1..4; default 1; >2 is ugly)
@ dotleak   - allow some dot crawl everywhere 
                (0-255; default 0; 32 is just visble; >64 is extreme)
@ csub      - default 2 (1=betacam; 2=VHS)
@ cblur     - default 0.3 (0.0=no added blur; 0.5=VHS)
@ lblur     - default 0.3
@ lnoise    - default 4 (0=bypass; 2=subliminal; 22-33=VHS)
@ cnoise    - default 4 (0=bypass; 2=subliminal; 33=VHS)
@ streaking - default 0.0 (1.0=extreme horizontal streaking)
@ rainbow   - rainbow effect opacity (default 0.2)
@ showargs  - if true, show the arguments as a Subtitle
@ threads   - cpu threads you want to use (default 4)
```

## Requisites

- **[AviSynth+](https://github.com/AviSynth/AviSynthPlus/releases)**
- **Plugins** *(need to be added onto the plugins folders on the AviSynth+ program folder)*
    - [MaskTools](https://github.com/pinterf/masktools/releases/)
    - [AddGrainC](https://github.com/pinterf/AddGrainC/releases)
    - [FFT3DFilter](https://github.com/pinterf/fft3dfilter/releases) *(need FFTW 3.3.5 dlls)*
    - [GRunT](https://github.com/pinterf/GRunT/releases)
    - [TEMmod](https://github.com/Asd-g/TEMmod/releases)

## Initial Contributions

- **@SaurusX** *(Doom9)* - (Helping with rainbowing)
- **@zarxrax** *(Doom9)* - (Contributing with rainbowing)

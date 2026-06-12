---
title: "Any working DVD-authoring software in 14.04 (Trusty)?"
date: 2016-06-12
forum: Multimedia Software
---

### Post by VanillaMozilla on 2016-06-12
DVDStyler is completely broken (GUI terminates), and the bug on it was simply closed, because it is supposed to be fixed in some future version.  Bombono is a great program, but it demands ffmpeg, which is unavailable for Trusty.

Heroic patches get to be rather old.  PPA's and recompiling smack of desperation, and can be a fool's errand.  I already updated from one LTS to another just to get one program fixed by PPA, but the update broke at least three other programs.

So just what do I do?  Does anyone have any info on working DVD authoring software?

---

### Post by VanillaMozilla on 2016-06-13
OK, I have a partial but unsatisfactory answer.  Devede works, as always, but it's quite limited.  It lacks menu editing, which I need.

According to the Bombono Web site, it might be calling for ubuntu-restricted-extras.  But, no, that doesn't solve the problem, and the support forum over there is gone.  And just so you know what's involved, installing that requires removing two other packages, which probably broke something else.  All undone, hopefully.

Suggestions?  Is there anything good that works on 14.04?

---

### Post by Adam_GUI on 2016-06-18
Not to get your hopes up, but, in for a penny.
Here's my "Me Too" Bug effects multiple users post.

On DVDStyler --
This caught my eye, as I could swear I had DVDStyler working in the past with 14.04.
I've since upgraded to 16.04.  DVDStyler is no longer included in the repos.  "Weird."

So, I tried to build it from source.
It has two program parts.  Styler and wxsvg.

wxsvg fails make with error 1.
Output for anyone checking over the work:
```
In file included from ../../include/wxSVG/SVGElement.h:18:0,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGAnimatedType.h:54:13: error: field ‘m_color’ has incomplete type ‘wxRGBColor {aka wxColour}’
  wxRGBColor m_color;
             ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/CSSStyleDeclaration.h:13:0,
                 from ../../include/wxSVG/SVGStylable.h:13,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/CSSValue.h: In constructor ‘wxCSSPrimitiveValue::wxCSSPrimitiveValue(const wxRGBColor&)’:
../../include/wxSVG/CSSValue.h:99:68: error: invalid use of incomplete type ‘wxRGBColor {aka class wxColour}’
       m_primitiveType(wxCSS_RGBCOLOR), m_color(new wxRGBColor(value)) {}
                                                                    ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/SVGPaint.h:12:0,
                 from ../../include/wxSVG/CSSStyleDeclaration.h:14,
                 from ../../include/wxSVG/SVGStylable.h:13,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGColor.h: At global scope:
../../include/wxSVG/SVGColor.h:31:16: error: field ‘m_rgbColor’ has incomplete type ‘wxRGBColor {aka wxColour}’
     wxRGBColor m_rgbColor;
                ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/SVGPaint.h:12:0,
                 from ../../include/wxSVG/CSSStyleDeclaration.h:14,
                 from ../../include/wxSVG/SVGStylable.h:13,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGColor.h: In constructor ‘wxSVGColor::wxSVGColor(wxRGBColor)’:
../../include/wxSVG/SVGColor.h:41:27: error: ‘color’ has incomplete type
     wxSVGColor(wxRGBColor color): wxCSSValue(wxCSS_SVG_COLOR),
                           ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/CSSStyleDeclaration.h:14:0,
                 from ../../include/wxSVG/SVGStylable.h:13,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGPaint.h: In constructor ‘wxSVGPaint::wxSVGPaint(wxRGBColor)’:
../../include/wxSVG/SVGPaint.h:47:27: error: ‘color’ has incomplete type
     wxSVGPaint(wxRGBColor color):
                           ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/SVGStylable.h:13:0,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/CSSStyleDeclaration.h: In member function ‘wxRGBColor wxCSSStyleDeclaration::GetColor() const’:
../../include/wxSVG/CSSStyleDeclaration.h:223:5: error: return type ‘wxRGBColor {aka class wxColour}’ is incomplete
     {
     ^
../../include/wxSVG/CSSStyleDeclaration.h:225:81: error: invalid use of incomplete type ‘wxRGBColor {aka class wxColour}’
  it != end() ? ((wxCSSPrimitiveValue&)*it->second).GetRGBColorValue() : wxRGBCo
                                                                     ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/SVGStylable.h:13:0,
                 from ../../include/wxSVG/SVGAElement.h:17,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/CSSStyleDeclaration.h:225:96: error: invalid use of incomplete type ‘wxRGBColor {aka class wxColour}’
  end() ? ((wxCSSPrimitiveValue&)*it->second).GetRGBColorValue() : wxRGBColor();
                                                                              ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from ../../include/wxSVG/SVGAElement.h:17:0,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGStylable.h: In member function ‘wxRGBColor wxSVGStylable::GetColor()’:
../../include/wxSVG/SVGStylable.h:65:34: error: return type ‘wxRGBColor {aka class wxColour}’ is incomplete
     inline wxRGBColor GetColor() { return m_style.GetColor(); }
                                  ^
In file included from ../../include/wxSVG/svg.h:95:0,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGDocument.h: At global scope:
../../include/wxSVG/SVGDocument.h:91:5: error: ‘wxImage’ does not name a type
     wxImage Render(int width = -1, int height = -1, const wxSVGRect* rect = NUL
     ^
In file included from ../../include/wxSVG/SVGCanvas.h:16:0,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGCanvasItem.h:198:2: error: ‘wxImage’ does not name a type
  wxImage m_image; /** image data */
  ^
../../include/wxSVG/SVGCanvasItem.h:216:2: error: ‘wxImage’ does not name a type
  wxImage GetImage(double time);
  ^
../../include/wxSVG/SVGCanvasItem.h:221:2: error: ‘wxImage’ does not name a type
  wxImage m_image;
  ^
In file included from SVGCanvasCairo.h:14:0,
                 from SVGCanvasCairo.cpp:11:
../../include/wxSVG/SVGCanvas.h:27:10: error: ‘wxImage’ does not name a type
  virtual wxImage GetImage() = 0;
          ^
../../include/wxSVG/SVGCanvas.h:28:65: error: invalid use of incomplete type ‘wxRGBColor {aka class wxColour}’
  virtual void Clear(wxRGBColor color = wxRGBColor(0xFF,0xFF,0xFF)) = 0;
                                                                 ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from SVGCanvasCairo.cpp:11:0:
SVGCanvasCairo.h:29:5: error: ‘wxImage’ does not name a type
     wxImage GetImage();
     ^
SVGCanvasCairo.h:30:57: error: invalid use of incomplete type ‘wxRGBColor {aka class wxColour}’
  void Clear(wxRGBColor color = wxRGBColor(0xFF,0xFF,0xFF));
                                                         ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
In file included from SVGCanvasCairo.cpp:14:0:
SVGCanvasImageCairo.h:19:36: error: expected ‘)’ before ‘image’
  wxSVGCanvasImageCairoData(wxImage image);
                                    ^
SVGCanvasCairo.cpp:58:1: error: ‘wxImage’ does not name a type
 wxImage wxSVGCanvasCairo::GetImage() {
 ^
SVGCanvasCairo.cpp: In member function ‘virtual void wxSVGCanvasCairo::Clear(wxRGBColor)’:
SVGCanvasCairo.cpp:82:41: error: ‘color’ has incomplete type
 void wxSVGCanvasCairo::Clear(wxRGBColor color) {
                                         ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
SVGCanvasCairo.cpp: In member function ‘void wxSVGCanvasCairo::SetPaint(cairo_t*, const wxSVGPaint&, float, wxSVGCanvasPathCairo&, wxSVGSVGElement&, const wxSVGMatrix&)’:
SVGCanvasCairo.cpp:239:14: error: variable ‘wxRGBColor color’ has initializer but incomplete type
   wxRGBColor color = paint.GetRGBColor();
              ^
SVGCanvasCairo.cpp: In member function ‘virtual void wxSVGCanvasCairo::SetStopValue(unsigned int, float, float, const wxRGBColor&)’:
SVGCanvasCairo.cpp:247:63: error: invalid use of incomplete type ‘const wxRGBColor {aka const class wxColour}’
  cairo_pattern_add_color_stop_rgba(m_pattern, offset, rgbColor.Red() / 255.0, r
                                                               ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
SVGCanvasCairo.cpp:247:87: error: invalid use of incomplete type ‘const wxRGBColor {aka const class wxColour}’
 _color_stop_rgba(m_pattern, offset, rgbColor.Red() / 255.0, rgbColor.Green() / 
                                                                     ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
SVGCanvasCairo.cpp:248:12: error: invalid use of incomplete type ‘const wxRGBColor {aka const class wxColour}’
    rgbColor.Blue() / 255.0, opacity);
            ^
In file included from ../../include/wxSVG/RGBColor.h:14:0,
                 from ../../include/wxSVG/SVGAnimatedType.h:13,
                 from ../../include/wxSVG/SVGElement.h:18,
                 from ../../include/wxSVG/SVGAElement.h:12,
                 from ../../include/wxSVG/svg.h:12,
                 from ../../include/wxSVG/SVGCanvasItem.h:14,
                 from ../../include/wxSVG/SVGCanvas.h:16,
                 from SVGCanvasCairo.h:14,
                 from SVGCanvasCairo.cpp:11:
/usr/include/wx-3.0/wx/colour.h:17:28: note: forward declaration of ‘wxRGBColor {aka class wxColour}’
 class WXDLLIMPEXP_FWD_CORE wxColour;
                            ^
SVGCanvasCairo.cpp: In member function ‘void wxSVGCanvasCairo::DrawCanvasImage(wxSVGCanvasImage&, cairo_surface_t*, wxSVGMatrix&, const wxCSSStyleDeclaration&, wxSVGSVGElement&)’:
SVGCanvasCairo.cpp:716:52: error: ‘class wxSVGCanvasImage’ has no member named ‘m_image’
  double scaleX = canvasImage.m_width / canvasImage.m_image.GetWidth();
                                                    ^
SVGCanvasCairo.cpp:717:53: error: ‘class wxSVGCanvasImage’ has no member named ‘m_image’
  double scaleY = canvasImage.m_height / canvasImage.m_image.GetHeight();
                                                     ^
SVGCanvasCairo.cpp:750:66: error: ‘class wxSVGCanvasImage’ has no member named ‘m_image’
   scaleY = scaleY * canvasImage.GetDefaultHeight() / canvasImage.m_image.GetHei
                                                                  ^
SVGCanvasCairo.cpp:759:42: error: ‘class wxSVGCanvasImage’ has no member named ‘m_image’
  cairo_rectangle(m_cr, 0, 0, canvasImage.m_image.GetWidth(), canvasImage.m_imag
                                          ^
SVGCanvasCairo.cpp:759:74: error: ‘class wxSVGCanvasImage’ has no member named ‘m_image’
 o_rectangle(m_cr, 0, 0, canvasImage.m_image.GetWidth(), canvasImage.m_image.Get
                                                                     ^
Makefile:400: recipe for target 'SVGCanvasCairo.lo' failed
make[2]: *** [SVGCanvasCairo.lo] Error 1

```

DVDStyler fails config asking for "libwx_gtk2u_media".
It will not accept the suggested libwxgtk-media3.0-0v5 in the repos.

I get the same output on the stable release from January 16 and the devel release from June 16.


On DeVeDe
I don't remember ever using this previously.
Upstream kinda has menu editing?  I mean, I could get used to this...  But I'll really miss DVDStyler.
[ATTACH=CONFIG]269647[/ATTACH]



On Bombono.
I agree with you.  This looks limited.
This is workable though.
[ATTACH=CONFIG]269648[/ATTACH]

Guess I can use either, now that I've moved up a version.

I know it can be little consolation for the version you're sitting at now.
Maybe as future options?

---

### Post by mc4man on 2016-06-18
If you want dvdstyler in 16.04 take a look here - [https://launchpad.net/~mc3man/+archive/ubuntu/check1](https://launchpad.net/~mc3man/+archive/ubuntu/check1)
(- there is a working version for 14.04 though not in a standalone ppa nor will it be.

Maybe someone will do a snap for 16.04 & later, ask on irc or wherever

---

### Post by Adam_GUI on 2016-06-19
> **mc4man said:**
> If you want dvdstyler in 16.04 take a look here - [https://launchpad.net/~mc3man/+archive/ubuntu/check1](https://launchpad.net/~mc3man/+archive/ubuntu/check1)
(- there is a working version for 14.04 though not in a standalone ppa nor will it be.

Maybe someone will do a snap for 16.04 & later, ask on irc or wherever

Well, hey!  Installs and runs on 16.04!
Thank you much.

---

### Post by VanillaMozilla on 2016-06-19
> **mc4man said:**
> ... dvdstyler ...
(- there is a working version for 14.04 though not in a standalone ppa nor will it be.

???  Where?

---

### Post by VanillaMozilla on 2016-06-19
> **Adam_GUI said:**
> On DVDStyler --
This caught my eye, as I could swear I had DVDStyler working in the past with 14.04.
I've since upgraded to 16.04.  DVDStyler is no longer included in the repos.  "Weird."
[https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374](https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374)


> **Adam_GUI said:**
> On Bombono.
I agree with you.  This looks limited.
This is workable though.
Bombono is a beautiful program, but it has a couple of small but solveable problems.  The first is that to edit a menu, etc. you have to select it *and then select the check mark.*  People didn't know about the check mark, so they assumed it didn't work and gave it bad reviews.  It was also a victim of frequent changes in libraries, which required frequent repairs and placed unreasonable demands on the one developer.  So now the problem seems to be a packaging problem:  the required ffmpeg library is not in the Ubuntu repository.  They're looking for maintainers now.  I hope they get someone.

I don't think any of my video editing programs are working, either.  **It would really, really help if they would just stop breaking programs.  Every time they change an API or discontinue a package it breaks programs.**

---

### Post by mc4man on 2016-06-19
> **VanillaMozilla said:**
> ???  Where?

Well I sensed you didn't want to use ppa's so didn't mention. Read the page carefully, any questions ask first.
[https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6)
(- I may be making some upgrades to the ppa in near future when I've the time.

---

### Post by Adam_GUI on 2016-06-19
> **VanillaMozilla said:**
> [https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374](https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1440374)



Bombono is a beautiful program, but it has a couple of small but solveable problems.  The first is that to edit a menu, etc. you have to select it *and then select the check mark.*  People didn't know about the check mark, so they assumed it didn't work and gave it bad reviews.  It was also a victim of frequent changes in libraries, which required frequent repairs and placed unreasonable demands on the one developer.  So now the problem seems to be a packaging problem:  the required ffmpeg library is not in the Ubuntu repository.  They're looking for maintainers now.  I hope they get someone.

I don't think any of my video editing programs are working, either.  **It would really, really help if they would just stop breaking programs.  Every time they change an API or discontinue a package it breaks programs.**

Believe me, I'm not unsympathetic.
PolyAudio/Pulseaudio bit hard.  Losing Gnome 2 for Unity had me jump spins. Splitting FFMPEG for LibVA was infuriating for production.

On FFMPEG, there's a PPA available for 14.04 that I used thanks to word through the folks distributing OBS.

sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
sudo apt-get update && sudo apt-get install ffmpeg

You may be glad to know that FFMPEG is back in the repositories of the next LTS up.  And that LibreOffice's layout has changed.  And that, if you need an NVidia driver, you'll have to disable splash in Plymouth and possibly sit through a full FSCK every boot if fastboot isn't enabled.

---

### Post by VanillaMozilla on 2016-06-20
> **mc4man said:**
> If you want dvdstyler in 16.04 take a look here - [https://launchpad.net/~mc3man/+archive/ubuntu/check1](https://launchpad.net/~mc3man/+archive/ubuntu/check1)
(- there is a working version for 14.04 though not in a standalone ppa nor will it be.

OK, that one is for 16.04, but somehow I missed this one.  Is there any problem with this one for 14.04?  [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler) .

I think I may pass on patching Bombono for now, since I don't really know what's needed, what library versions, etc.  In other words, I don't know what I'm doing, and there's potential for conflict in the libraries.

---

### Post by mc4man on 2016-06-20
> **VanillaMozilla said:**
> OK, that one is for 16.04, but somehow I missed this one.  Is there any problem with this one for 14.04?  [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler) .

I think I may pass on patching Bombono for now, since I don't really know what's needed, what library versions, etc.  In other words, I don't know what I'm doing, and there's potential for conflict in the libraries.
Should be ok, you'd need to try it & see.

---

### Post by VanillaMozilla on 2016-06-22
OK, thanks very much, guys.  By the way, if anyone asks you, Bombono and others would seem to be very candidates for AppImage distribution.  When the packaging system fails, it's nice to have an alternative.

---

### Post by VanillaMozilla on 2016-11-07
It's time for a follow-up.  Bombono actually works in version Ubuntu 16.04, and it works well.  I'm going to take this opportunity for a very brief review.

Overall, it's probably the best Linux software I have found for authoring video DVDs.  It's clean, straightforward, and well thought out.  It's flexible and produces beautiful videos.  It works as a front end to DVDAuthor.  There is also a Windows version that may be worth considering.  It's a beautiful program, and I can recommend it.

I want to spend most of the time describing a few quirks.  First, to edit a menu or view a resource, you have to select it and *then* click on the check mark.  Users may not know this, and they will probably think (wrongly) that the program doesn't work at all.  There is a reason for this:  it's to prevent unwanted rendering that may hurt performance.

The program places files in a user-selected location, and the contents of this directory will be deleted.  The program does warn users, but the warning is perhaps not scary enough to warn some users.

For me the most serious problem is that the user has no control over which button is first selected (by default) on a menu.  In theory you can edit DVDAuthor.xml to make fine changes, and then run scons to reconstruct the DVD.  Fortunately, the file is documented, so that should be feasible, albeit not very convenient.

The program is inclined to corrupt its data or crash under certain conditions.  It's usually fine under ordinary conditions, but it can crash if you move files to other directories or make major changes such as removing a lot of menus and files from the project.

---


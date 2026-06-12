---
title: "Kdenlive crash at startup"
date: 2016-06-10
forum: Multimedia Software
---

### Post by lesyalouky on 2016-06-10
Just today I wanted to use Kdenlive after changing my icons and theme (using custom now) on Ubuntu 16.04(dont know if the custom icons have anything to do with it, but it was my first thought)
Got this strange output in Terminal, followed by the Kdenlive app coming up, but frozen, and crashing after a few seconds.
EDIT: I went back to stock icons and theme, but still the same output when running Kdenlive.

> sudo kdenlive
Icon theme "oxygen" not found.
Icon theme "oxygen" not found.
Error: standard icon theme "oxygen" not found!
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
QWidget::setMaximumSize: (/QToolButton) Negative sizes (2,-2) are not possible
Removing cache at "/home/whitehand/.cache/kdenlive-thumbs.kcache"
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
OpenGL vendor:  "X.Org"
OpenGL renderer:  "Gallium 0.4 on AMD TONGA (DRM 3.1.0, LLVM 3.8.0)"
OpenGL ARG_SYNC:  true
OpenGL OpenGLES:  false
OpenGL vendor:  "X.Org"
OpenGL renderer:  "Gallium 0.4 on AMD TONGA (DRM 3.1.0, LLVM 3.8.0)"
OpenGL ARG_SYNC:  true
OpenGL OpenGLES:  false
 Unauthorized access to memory(SIGSEGV) (core dumped [memory image saved])





Thank you for reading this far.


EDIT: So I've managed to install the oxygen icon theme with
> [COLOR=#FF0040]sudo apt-get install kde-runtime[/COLOR]
now the terminal output is the same, but without the missing oxygen icons.
Still crashes after a second.

---

### Post by shantiq on 2016-06-14
if you install from the repository  try this instead

```
 sudo add-apt-repository ppa:sunab/kdenlive-release
```
```
sudo apt-get update && sudo apt-get install kdenlive
```


and see if this version works fine; often the repository version crashes

try it maybe

---

### Post by lesyalouky on 2016-06-18
> **shantiq said:**
> if you install from the repository  try this instead

```
 sudo add-apt-repository ppa:sunab/kdenlive-release
```
```
sudo apt-get update && sudo apt-get install kdenlive
```


and see if this version works fine; often the repository version crashes

try it maybe

Thank you so much! You are THE man. It works now.

---


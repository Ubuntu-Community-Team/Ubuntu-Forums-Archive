---
title: "Krita Krashing"
date: 2018-12-17
forum: Multimedia Software
---

### Post by penciltester on 2018-12-17
Hi everyone I have installed Ubuntu 18.04 on my Surface pro 3. I was exited to see Krita working for all of about a minute. This is what gets thrown out in terminal. any help would be very much appreciated.Thanks

```

  	 	 	 	   QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
 /tmp/.mount_krita.lUNdVz/usr/lib/krita-python-libs/krita added to PYTHONPATH
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Bold")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Light")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/edit-clear
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/opacity-decrease
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/opacity-increase
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/lightness-increase
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/lightness-decrease
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/zoom-in
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/rotate-canvas-left
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/rotation-reset
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/rotate-canvas-right
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/zoom-out
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/brushsize-decrease
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/brushsize-increase
 file:///tmp/.mount_krita.lUNdVz/usr/lib/qml/org/krita/sketch/components/Button.qml:84:9: QML Image: Failed to get image from provider: image://icon/preset-switcher
 QXcbConnection: XCB error: 148 (Unknown), sequence: 1054, resource id: 0, major code: 140 (Unknown), minor code: 20
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Bold")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Light")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 QXcbConnection: XCB error: 148 (Unknown), sequence: 1078, resource id: 0, major code: 140 (Unknown), minor code: 20
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Bold")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Light")
 krita.general: Could not find font QVariant(QString, "Source Sans Pro") with style QVariant(QString, "Regular")
 krita.lib.flake: "InteractionTool" : action "object_order_lower" conflicts with canvas action "rotate_canvas_left" shortcut: "Ctrl+["
 krita.lib.flake: "InteractionTool" : action "object_order_raise" conflicts with canvas action "rotate_canvas_right" shortcut: "Ctrl+]"
 krita.lib.flake: "InteractionTool" : action "object_order_lower" conflicts with canvas action "rotate_canvas_left" shortcut: "Ctrl+["
 krita.lib.flake: "InteractionTool" : action "object_order_raise" conflicts with canvas action "rotate_canvas_right" shortcut: "Ctrl+]"
 QPainter::begin: Paint device returned engine == 0, type: 3
 QPainter::setCompositionMode: Painter not active
 QPainter::begin: Paint device returned engine == 0, type: 3
 QPainter::setCompositionMode: Painter not active
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(LeftButton)
 krita.lib.flake: "InteractionTool" : action "object_order_lower" conflicts with canvas action "rotate_canvas_left" shortcut: "Ctrl+["
 krita.lib.flake: "InteractionTool" : action "object_order_raise" conflicts with canvas action "rotate_canvas_right" shortcut: "Ctrl+]"
 krita.lib.flake: "InteractionTool" : action "object_order_lower" conflicts with canvas action "rotate_canvas_left" shortcut: "Ctrl+["
 krita.lib.flake: "InteractionTool" : action "object_order_raise" conflicts with canvas action "rotate_canvas_right" shortcut: "Ctrl+]"
 QPainter::begin: Paint device returned engine == 0, type: 3
 QPainter::setCompositionMode: Painter not active
 QPainter::begin: Paint device returned engine == 0, type: 3
 QPainter::setCompositionMode: Painter not active
 ===
 WARNING: Tracked tablet buttons are not consistent!
 tabletData->buttons = QFlags<Qt::MouseButtons>(NoButton)
 expectedButtons = QFlags<Qt::MouseButtons>(Left
```

---

### Post by penciltester on 2018-12-20
Nevermind. It is some malfunction of my active pen that the surface devices use.

---


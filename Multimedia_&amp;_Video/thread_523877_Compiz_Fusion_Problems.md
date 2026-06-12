---
title: "Compiz Fusion Problems"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by circuz_phreak on 2007-08-12
Installed compiz from a how to, then installed compiz fusion from a how to.  Everything seems to be working but my cube is only 2-D even though i have four workspaces going.  Also i get this output when running compiz --replace.  Seems to be a problem with wobbly (which seems to be working fine so far), and window decorator (could that be the source of my cube problems?)  Any help would be awesome!

```

mike@mike-ubuntu:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin crashhandler (crashhandler)
Adding plugin imgjpeg (imgjpeg)
Adding plugin glib (glib)
Adding plugin snap (snap)
Adding plugin cubereflex (cubereflex)
Adding plugin plane (plane)
Adding plugin decoration (decoration)
Adding plugin screenshot (screenshot)
Adding plugin animation (animation)
Adding plugin inotify (inotify)
Adding plugin rotate (rotate)
Adding core settings (General Options)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin fadedesktop (fadedesktop)
Adding plugin wall (wall)
Adding plugin blur (blur)
Adding plugin svg (svg)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin ezoom (ezoom)
Adding plugin gears (gears)
Adding plugin extrawm (extrawm)
Adding plugin clone (clone)
Adding plugin switcher (switcher)
Adding plugin zoom (zoom)
Adding plugin expo (expo)
Adding plugin annotate (annotate)
Adding plugin splash (splash)
Adding plugin bench (bench)
Adding plugin vpswitch (vpswitch)
Adding plugin workarounds (workarounds)
Adding plugin fade (fade)
Adding plugin showdesktop (showdesktop)
Adding plugin trailfocus (trailfocus)
Adding plugin cube (cube)
Adding plugin resizeinfo (resizeinfo)
Adding plugin resize (resize)
Adding plugin ring (ring)
Adding plugin addhelper (addhelper)
Adding plugin fs (fs)
Adding plugin put (put)
Adding plugin winrules (winrules)
Adding plugin png (png)
Adding plugin mblur (mblur)
Adding plugin group (group)
Adding plugin thumbnail (thumbnail)
Adding plugin neg (neg)
Adding plugin scaleaddon (scaleaddon)
Adding plugin gotovp (gotovp)
Adding plugin regex (regex)
Adding plugin scalefilter (scalefilter)
Adding plugin opacify (opacify)
Adding plugin text (text)
Adding plugin video (video)
Adding plugin reflex (reflex)
Adding plugin place (place)
Adding plugin scale (scale)
Adding plugin wobbly (wobbly)
Adding plugin water (water)
Initializing core options...done
Initializing decoration options...done
Initializing minimize options...done
Initializing move options...done
Initializing zoom options...done
Initializing workarounds options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing place options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)
Initializing cube options...done

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8283): Wnck-WARNING **: Unhandled action type (nil)
Initializing scale options...done
Initializing rotate options...done
Initializing switcher options...done
Setting Update "cursor_theme"

```

---


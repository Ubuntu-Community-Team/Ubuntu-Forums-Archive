---
title: "KDE / Gnome Fonts - DPI"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by duren on 2006-11-19
This is one of those FYI threads for anyone having problems with font sizes and wants to solve them with minimal effort / hours spent.

1. Add the following like under the Monitor section in your xorg.conf file: DisplaySize 328 246

Explanation: This forces xorg's DPI to something most people are used to, coming from windows as opposed to a calculated DPI based on resolution.

Effect: This implies a DPI of 75 I believe. It also means that fonts of size 10, 12 etc correspond to the same sizes in Windows. It also means that KDM and GDM will properly display prompts at the right sizes even if there are large resolutions defined in your xorg (ie everything is not so tiny). It eliminates the need to remove those high resolutions from your xorg.conf.

Original Source: [http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

----

2. Ensure that you have selected "Use my KDE fonts in GTK applications" inside "GTK Style and Fonts" (Settings -> Appearance & Themes) if you use KDE

Explanation: This will ensure that gnome applications use the same font settings as KDE in terms of font and size. If this setting doesn't work, try forcing a font and size that matches what you have selected as your general font in the standard fonts configuration for KDE. It may also be necessary to fire up gnome-font-properties and check that the DPI is also set to 75 in the details section.

Original Source: [http://ubuntuforums.org/showthread.php?t=47953&highlight=gtk+styles+fonts](http://ubuntuforums.org/showthread.php?t=47953&highlight=gtk+styles+fonts)

----

3. Firefox is the only application so far that seems to ignore these font settings for the UI. The problem I ran into was large letters. Edit your profile's prefs.js and add the following line:

Firefox 2.0: user_pref("layout.css.dpi", 0);
Firefox 1.5: user_pref("browser.display.screen_resolution", 0);

Effect: Firefox's UI font should now match its counterparts - I checked Thunderbird.

Original Source: [http://kb.mozillazine.org/Layout.css.dpi](http://kb.mozillazine.org/Layout.css.dpi)

----

Please remember to edit the prefs file while the browser is closed (otherwise all changes are lost) and to restart X to see the monitor section changes as well. This should help many of you with your font issues.

Regards,

---

### Post by gustolove on 2006-11-20
This is something that i see asked about a lot on the forums... maybe deserves a sticky? or a link to in one of the stickies?

just an idea.

---


---
title: "None of the audio profiles work in Sound Juicer"
date: 2012-05-11
forum: Multimedia Software
---

### Post by peterdm on 2012-05-11
Steps to reproduce:
[LIST]
[*]Start Sound Juicer
[/LIST]

Expected:
[LIST]
[*]Sound Juicer starts up and CD extraction works.
[/LIST]

What actually happens:
[LIST]
[*]I get an error dialog "The currently selected audio profile is not available on your installation." and the choice to select another profile or quit. Whatever I do, I cannot get CD extraction to work.
[*]When I select any profile from the suggested list I get the same error dialog. None of flac/mp3/ogg/... work.
[*]I reinstalled all packages that seemed relevant: sound-juicer, gstreamer good/bad/ugly, flac, gnome-media-profiles and libs... to no avail.
[*]Used gconf-editor to inspect the profiles in system/gstreamer/0.10/audio/profiles, there are several profiles there. Their names do not match the names of the profiles in Sound Juicer though, maybe that is a problem? For example, Sound Juicer has a profile "FLAC", but the Gnome profile is called "cdlossless".
[/LIST]

Any suggestions?

---


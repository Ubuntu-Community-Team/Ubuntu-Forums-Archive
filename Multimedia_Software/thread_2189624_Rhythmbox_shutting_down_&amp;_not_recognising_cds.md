---
title: "Rhythmbox shutting down &amp; not recognising cds"
date: 2013-11-23
forum: Multimedia Software
---

### Post by Luddite Savant on 2013-11-23
Hi, I've had a problem for a while of rhythmbox often shutting down when first started & then randomly thereafter. I've now noticed it's also not recognising cds at all.
I'm running Ubuntu 12.04 & Rhythmbox 2.97

Started from the command line Rhythmbox gives the following outputs:

> (rhythmbox:26292): libpeas-WARNING **: audiocd: /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so: undefined symbol: discid_get_submission_url

(rhythmbox:26292): libpeas-WARNING **: Could not load plugin module: 'audiocd'

(rhythmbox:26292): libpeas-WARNING **: Error loading plugin 'audiocd'

(rhythmbox:26292): Rhythmbox-WARNING **: Could not open device /dev/radio0

(rhythmbox:26292): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(rhythmbox:26292): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
^C
blank@Blank:~$ rhythmbox

(rhythmbox:26368): libpeas-WARNING **: audiocd: /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so: undefined symbol: discid_get_submission_url

(rhythmbox:26368): libpeas-WARNING **: Could not load plugin module: 'audiocd'

(rhythmbox:26368): libpeas-WARNING **: Error loading plugin 'audiocd'

(rhythmbox:26368): Rhythmbox-WARNING **: Could not open device /dev/radio0



I've already tried > sudo add-apt-repository ppa:webupd8team/rhythmbox && sudo apt-get update 
sudo apt-get install rhythmbox
but with no diference.

The command line output is over my head & I don't know what it's telling me (I think it's a plugin issue but that's likely not all) so can someone let me know what the issue is and what I can do to fix it?

---

### Post by Luddite Savant on 2013-11-27
Bump as I've not been able to find any solutions, hoping someone can help.

---

### Post by Luddite Savant on 2013-11-28
I've now tried removing rhythmbox and reinstalling it, but still no success. Get the following output now:

>    blank@Blank:~$ rhythmbox

(rhythmbox:8391): libpeas-WARNING **: audiocd: /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so: undefined symbol: discid_get_submission_url

(rhythmbox:8391): libpeas-WARNING **: Could not load plugin module: 'audiocd'

(rhythmbox:8391): libpeas-WARNING **: Error loading plugin 'audiocd'

(rhythmbox:8391): Rhythmbox-WARNING **: Could not open device /dev/radio0

** (rhythmbox:8391): CRITICAL **: totem_pl_parser_parse_with_base: assertion `strstr (uri, "://") != NULL' failed
Segmentation fault (core dumped)



---


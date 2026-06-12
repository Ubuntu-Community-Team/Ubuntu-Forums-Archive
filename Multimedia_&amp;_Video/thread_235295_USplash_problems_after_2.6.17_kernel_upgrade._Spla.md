---
title: "USplash problems after 2.6.17 kernel upgrade. Splashy not working"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by phenolholic on 2006-08-12
Hello,
I recently installed 2.6.17.7 and as a result, my usplash is not working. All I get is a blank screen, which then goes into X after the boot sequence. I tried installing splashy, and that didn't help much either. Same thing with splashy, just a blank screen. Can someone give me the rundown on installing usplash from scratch? I've found threads here and there but none seemed to have worked. So I would like the entire process from scratch if possible. TIA

---

### Post by Ziox on 2006-08-12
> **phenolholic said:**
> Hello,
I recently installed 2.6.17.7 and as a result, my usplash is not working. All I get is a blank screen, which then goes into X after the boot sequence. I tried installing splashy, and that didn't help much either. Same thing with splashy, just a blank screen. Can someone give me the rundown on installing usplash from scratch? I've found threads here and there but none seemed to have worked. So I would like the entire process from scratch if possible. TIA

Did you follow this guide: [http://www.ubuntuforums.org/showthread.php?t=216597&highlight=howto+splashy](http://www.ubuntuforums.org/showthread.php?t=216597&highlight=howto+splashy)

and perhaps you need to recompile splashy everytime the kernel is updated...

---

### Post by phenolholic on 2006-08-13
I did follow it but had no luck. I tried using the splashy_config -i and -s arguments and got this response:

(process:4955): GLib-CRITICAL **: g_ascii_strncasecmp: assertion `s1 != NULL' failed

(process:4955): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

(process:4955): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
Splashy ERROR: Setting XML file to <</theme.xml>> failed. XML File not found
Missing arguments
usage: splashy_config [option] arg
[-h, --help][-s, --set-theme THEME][-i, --install-theme THEME.tar.gz]
[-r, --remove-theme THEME][--info][-c, --create-theme  [args...]][-g, --get-key XPATH]
See --help for more information



Also, I even tried moving the config.xml from the theme I wanted to use into /etc/splashy and still got a blank screen.

---

### Post by spoiled on 2006-08-16
I also have the same problem with a blank screen after upgrading to 2.6.17. However I dont seem to have the same problem with splashy_config as you do.
Which version of splashy are you using?

I tried using; splashy_config -s <name_of_theme_dir> and that seemed to work fine, please note that even though I set the theme correctly it didnt work at boot time..

---


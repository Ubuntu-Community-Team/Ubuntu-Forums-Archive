---
title: "Brasero Closes Unexpectedly While Burning Video Project"
date: 2010-11-02
forum: Multimedia Software
---

### Post by krishnandu.sarkar on 2010-11-02
Hey guys, when I try to burn a video project, brasero closes unexpectedly when I click "burn".

Though it works fine for ISO Burning, Data Project, Audio Project, CD/DVD Copy.

Well...to find out more I started brasero in Terminal and this was the output.

```
krishnandu@krishnandu-desktop:~$ brasero

** (brasero:4124): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:4124): GLib-CRITICAL **: g_variant_builder_end: assertion `is_valid_builder (builder)' failed

(brasero:4124): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(brasero:4124): GLib-CRITICAL **: g_variant_type_is_array: assertion `g_variant_type_check (type)' failed

(brasero:4124): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'
aborting...
Aborted
krishnandu@krishnandu-desktop:~$ 

 
```

Please help...what's wrong??

And one more question, Do I need anything else to create Video DVD's and Video CD's(playable in CD / DVD players) from different file formats..??

BTW I've ubuntu-restricted-extras installed and I can play any files without any hassle.

NB :  I know many people would say Brasero sucks use K3b, I know k3b works fine, but I want to solve this issue.

---

### Post by bean72 on 2010-11-02
i have the same problem when I copy CD's. I installed gnomebaker, and i can get further in the burning process when I try to copy using brasero, but I still get an error. Here is the log output
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2862)
```
For now I'm gonna use gnomebaker for my cd burning software, it seems to be alot better.

---

### Post by krishnandu.sarkar on 2010-11-03
So many views and no replies..!! Ok reporting it as a bug.

---

### Post by mark2741 on 2010-12-24
Same here. I tried multiple times to burn a set of video files to DVD and every time I click the 'Burn...' button Brasero just shuts down immediately.

---


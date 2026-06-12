---
title: "Brasero DVD video project. I Click &quot;Burn&quot; and Brasero disappears like magic!"
date: 2010-12-17
forum: Multimedia Software
---

### Post by grog11911 on 2010-12-17
I need this done for a present soon!!! This is my first time creating a video DVD from other video files. I drag and dropped 2 .flv files to the area where it tells you to drag them. They appeared there. Then I clicked "Burn..." and brasero disappeared. I ran it in terminal and this is what I got:

```
$ brasero

** (brasero:5843): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:5843): GLib-CRITICAL **: g_variant_builder_end: assertion `is_valid_builder (builder)' failed

(brasero:5843): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(brasero:5843): GLib-CRITICAL **: g_variant_type_is_array: assertion `g_variant_type_check (type)' failed

(brasero:5843): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'
aborting...
Aborted

```

---

### Post by sanderj on 2010-12-17
Did you Google for it? I did: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/665166](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/665166) : note the "cdrdao" at the end of the thread.

---

### Post by Drooling_Sheep on 2010-12-17
I have the same problem when trying to burn a DVD video. I installed cdrdao and nothing changed.

---

### Post by twschmidt on 2011-02-01
"sudo apt-get install libdvdread4; sudo /usr/share/doc/libdvdread4/install-css.sh"

This fixed the problem for my 10.10 i386 installation.

---

### Post by DexterP17 on 2011-02-04
I had the same problem but I found the answer in help and support. in order to get Brasero to burn DVDs you have to install this: DVDauthor in Ubuntu Software Center or in Synaptic and it should let you burn video DVDs now. Hope I was some help to you!

---

### Post by JC Cheloven on 2011-02-04
Hopefully Brasero will fix this that and such at some time. In the meanwhile, I'd suggest to use GnomeBaker. It works fine for me.

---


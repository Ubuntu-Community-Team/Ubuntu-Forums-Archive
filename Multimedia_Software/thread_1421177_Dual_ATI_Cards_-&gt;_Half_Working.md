---
title: "Dual ATI Cards -&gt; Half Working"
date: 2010-03-03
forum: Multimedia Software
---

### Post by jtdeloach10 on 2010-03-03
System:
ATI RADEON 3450 HD ( 1x DVI, 1x VGA, 1x HDMI ) [ pci-e x16 ]
ATI 9200 PRO ( 1x DVI, 1x VGA ) [ pci ]

Currently:
I can get two of the montiors working at a time, not both sets. However on the none working I get "113-PAC78H06-00R-HT-R1 R9250 128M\64B CRT\TV\DVI-I 166M\240E" I believe that represents some data from the 9200, that however is being outputted on the 3450.

The question:
How can I get both cards ( 4 monitors total ) working together? I am using the default "ati" driver as the fglrx isn't working as good.


Info:
[http://pastebin.ubuntu.com/388033/](http://pastebin.ubuntu.com/388033/) [ lspci ]
[http://pastebin.ubuntu.com/388034/](http://pastebin.ubuntu.com/388034/) [ xorg.0.log ]
[http://pastebin.ubuntu.com/388031/](http://pastebin.ubuntu.com/388031/) [ xorg.conf ]

---

### Post by jtdeloach10 on 2010-03-04
frusterated. bump.

---

### Post by jtdeloach10 on 2010-03-04
I have posted 5 questions in the past month and **none** of them have been answered! PLEASE!

BUMP!

---

### Post by Mark Phelps on 2010-03-05
Sorry ... don't have a solution but do have a suggestion ...

What's going to hamper you in whatever you do to solve this is that the 9200 does not have ATI Linux drivers anymore -- and is not going to.  ATI dropped Linux driver support for that card a long time ago.

The Phoronix forums have an open source ATI driver forum where they do a lot of testing and tweaking.  If you check there, you may find some settings you can tweak to do what you want.

---


---
title: "Permanently selecting default sound output."
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by themainliner on 2007-07-06
Ah, this sounds churlish...a mere detail. :D

Ubuntu has correctly detected and will use both my enabled onboard sound chip: NVidia CK804 and PCI expansion card: Creative Audigy eX.  I can use both sound out/inputs. I can switch between them without issues. I should be happy and I am. ;)

However, I want to use the Audigy as the default playback and after every reboot the system defaults to the onboard sound.  I am pretty sure that the solution is a straightforward bit of config file editing...but which file needs which entry? :confused:

After having Feisty, Automatix and simple64 all conspire to have me connected to the Internet, using both my TFTs in Twinview, playing games through Cedega and Wine and listening to all my mp3 OUT OF THE BOX nearly, this seems to me a very minor complaint.  I added this last paragraph for any Windows wavers who are still thinking that Linux is still difficult.  :popcorn:

---

### Post by PgR on 2007-07-06
Does this help?

[http://doc.gwos.org/index.php/Multisounds/](http://doc.gwos.org/index.php/Multisounds/)

---

### Post by PgR on 2007-07-06
Does this help?

[http://doc.gwos.org/index.php/Multisounds/](http://doc.gwos.org/index.php/Multisounds/)

Or 

```
asoundconf list
asoundconf set-default-card <card>
```

---

### Post by themainliner on 2007-07-06
Thanks, dude.

I knew it would  be simple and that was:
```
asoundconf list
asoundconf set-default-card
```
sorted my small problem out. :KS

---


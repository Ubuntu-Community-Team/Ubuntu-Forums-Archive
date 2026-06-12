---
title: "Very quiet sound 9.04"
date: 2009-09-08
forum: Multimedia Software
---

### Post by Darkebrz on 2009-09-08
Well, this problem has been really buggin me since dual booting Ubuntu. At first I though that there was no audio, but if I turned EVERYTHING to its highest, I can only hear a faint whisper.
I am using Ubuntu 9.04.
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I would really appreciate some help on this, and on0bi on the IRC has done everything he could with no sucess. ;_;

---

### Post by dynamics on 2009-09-08
I don't know whether this will work or not but you may give it a try because it is easy to test.

System > Preferences > Sound 
Go to 'Devices' tab and toggle first two options to ALSA

Now open terminal and enter

$ alsamixer

You will get a graphical volume controller in the terminal itself. Use 'left' / 'right' arrows to navigate between volume controllers and 'up'/'down' arrows to increase/decrease volume.

'Esc' to quit.

Good luck :-)

---

### Post by Darkebrz on 2009-09-09
> **dynamics said:**
> I don't know whether this will work or not but you may give it a try because it is easy to test.

System > Preferences > Sound 
Go to 'Devices' tab and toggle first two options to ALSA

Now open terminal and enter

$ alsamixer

You will get a graphical volume controller in the terminal itself. Use 'left' / 'right' arrows to navigate between volume controllers and 'up'/'down' arrows to increase/decrease volume.

'Esc' to quit.

Good luck :-)
Already tried this.
Also, I think this should be filed under [ubuntu], sorry.

---


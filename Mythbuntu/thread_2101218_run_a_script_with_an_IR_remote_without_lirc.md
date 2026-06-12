---
title: "run a script with an IR remote without lirc"
date: 2013-01-04
forum: Mythbuntu
---

### Post by lmclaren on 2013-01-04
Hi,

I have moved to using my remote by a combination of loadkeys with a keymap and remapping keycodes with evdev.

Seems to be working a lot smoother now but I have one thing left I need to do, I would like to receive a remote control press and have that run a .sh scrip to adjust the volume on the tv etc.

All the scripts are pre existing and already work, I just can't work out how to run a script from a remote press.

I am using a microsoft compatible remote.

any suggestions?

regards

Lee

---

### Post by AlecJ on 2013-01-04
I'm interested to know why you moved?

I'm using .26 on 12.04 and a mceusb remote, only yesterday I discovered that F7 from my keyboard brings up Teletext from the BBC from Astra.
This meant adding the F7 key to the Teletext button on my remote,
with irw in a terminal and mousepad editing ~/.mythtv/lircrc
I assigned the missing keys to the unused buttons.

I used to run a script from the remote, to restart the frontend after a crash or whatever, no need nowdays, but that it was an entry in ~/.mythtv/lircrc like this:-

begin
    remote = mceusb
    prog = irexec
    button = Power
    config = /usr/sbin/runmyth
    repeat = 0
    delay = 0
end 

is there not a keymap file similar anywhere?

---

### Post by lmclaren on 2013-01-04
The main reason was speed, lirc has served me well for many years but has always been a little slower than say using the keyboard.

Using keymap is about half way between lirc and a keyboard, so it feels a lot better.

The main performance increase is 'felt' on an acer revo.

---

### Post by AlecJ on 2013-01-04
As a remote frontend?
How does it perform?

---

### Post by lmclaren on 2013-01-05
mine has an ssd instead of the original hdd, hole cut in the side for better air flow so it is not too bad at all, resumes in about 5 secs.

I would go an ion2 nowadays, try to find a fanless for best results.

---

### Post by topcat5 on 2013-01-06
You can create a script.  Assign it to a hot key in XFCE, then map your remote to that hotkey.

---


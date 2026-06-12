---
title: "Trouble getting Toshiba Laptop Audio working properly"
date: 2010-04-23
forum: Multimedia Software
---

### Post by jervin2 on 2010-04-23
So, help me through getting my audio working properly on my Toshiba Satellite A105-S2081 Laptop.  I think I've been through most of the help messages and tried many things to get it working correctly.  The ONLY thing that has helped is to go to /etc/modprobe.d/alsa-base.conf and change model=auto to model=generic. 

(options snd-hda-intel power_save=10 power_save_controller=N model=generic)

I've tried model=toshiba, model=auto, model=lenovo, model=3stack, model=dallas and the laptops internal sound device disappears from the list of sound devices.  If I plug in my Logitech Headset, it seems to work fine.

It also seems to work fine if I boot it up into XP SP3.

It does work now generally with model=generic, but not sure that everything works properly, like the headset & microphone jack.  (Actually the reason I have the Logitech Headset is because the headset jack doesn't work).

Thank you for any suggestions. 

Ubuntu 9.10
Realtek ID 861
Toshiba Satellite A105-S2081

---

### Post by Alan James on 2010-04-24
What is the audio actually doing when the headset isn't plugged in? Is it cracking? Is it static? Is there no audio at all? Please give more detail as to what &#8220;not working&#8221; means.
 

 Also, how does the headset work when the headset jack does not work? I'm sure this is just mis-communication, but I really need to clarify before being able to help.

---

### Post by lisati on 2010-04-24
> **jervin2 said:**
> So, help me through getting my audio working properly on my Toshiba Satellite A105-S2081 Laptop.  I think I've been through most of the help messages and tried many things to get it working correctly.  The ONLY thing that has helped is to go to /etc/modprobe.d/alsa-base.conf and change model=auto to model=generic. 

(options snd-hda-intel power_save=10 power_save_controller=N model=generic)

I've tried model=toshiba, model=auto, model=lenovo, model=3stack, model=dallas and the laptops internal sound device disappears from the list of sound devices.  If I plug in my Logitech Headset, it seems to work fine.

It also seems to work fine if I boot it up into XP SP3.

It does work now generally with model=generic, but not sure that everything works properly, like the headset & microphone jack.  (Actually the reason I have the Logitech Headset is because the headset jack doesn't work).

Thank you for any suggestions. 

Ubuntu 9.10
Realtek ID 861
Toshiba Satellite A105-S2081
When I had 7.04* on a Toshiba Satellite A100, the sound didn't work "out of the box", and I found that it started working once I applied all available updates. 
I've found that 10.04 looks promising on my current laptop, a Toshiba Satellite M200.

[*]7.04 noticed in the OP's profile. Is this correct?

---

### Post by jervin2 on 2010-04-24
OK, the basic sound works fine with model=generic defined.  It doesn't work with any of the other more normal settings.  Meaning that it doesn't show up as a device in the Sound Preferences unless I specify model=generic.  I can live with it that way if it's the only setting that I can get to work, I just can't believe that it should be set that way.

---

### Post by Yellow Pasque on 2010-04-24
Have you tried model=hp ?
Some Toshiba Satellites have similar BIOS to HP's (e.g. [http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=blob;f=doc/ChangeLog;h=38749b9cd76fb8030d3b9b0133d86572dd6ab199;hb=HEAD](http://omnibook.git.sourceforge.net/git/gitweb.cgi?p=omnibook/omnibook;a=blob;f=doc/ChangeLog;h=38749b9cd76fb8030d3b9b0133d86572dd6ab199;hb=HEAD) )

---

### Post by jervin2 on 2010-04-24
Nope, model=hp didn't work either.  in sound preferences, I click on the output tab and it only lists simultaneous output stereo which comes in when I start PulseAudio Device Chooser which also doesn't see the internal audio device.  As before, when I plug in my Logitech USB Headset, it appears too, but not the internal laptop sound.

---

### Post by jervin2 on 2010-04-24
On the efficient side, I did find that I can issue the command "sudo alsa force-reload" rather than restarting ubuntu when I change the model= setting.

---


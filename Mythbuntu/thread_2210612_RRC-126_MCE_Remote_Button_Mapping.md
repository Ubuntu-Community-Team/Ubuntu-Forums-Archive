---
title: "RRC-126 MCE Remote Button Mapping"
date: 2014-03-11
forum: Mythbuntu
---

### Post by kyle17 on 2014-03-11
I found out that by default Mythbuntu recognizes my IR remote so that there is no need to install LIRC.  However I would like change some of the button mappings and am not sure where to look.  Namely, I would like the OK button to be recognized as the Enter button.

I tested with [FONT=Ubuntu Mono]sudo showkey -s

[/FONT]and OK was not even recognized on input.   I have plenty of linux experiance, just new with Mythbuntu.

---

### Post by khPWXxF on 2014-03-12
You may find that lirc is actually running if you specified your remote in mythtv setup.
I was very confused with lirc (still am on occasions!) but the controlling files with 12.04 are:

1.  /etc/lirc/hardware.conf  tells lirc where to find the IR receiver.
2.  /etc/lirc/lirc.conf      tells lirc about the timing of the pulses and gives the keypress names (eg KEY_UP)       
         to a particular train of pulses.
3.  ~/.mythtv/lircrc is a translation table between those keypress names and which key to be put into which system (eg myth)
4.  The keybindings (frontend setup) define which keys do what in any state.

You may need to chase down a trail of links or 'include' statements with these files.
Use irw to find the keypress names.  Quit with ^C

hth
Phil

---

### Post by kyle17 on 2014-03-12
> **khPWXxF said:**
> You may find that lirc is actually running if you specified your remote in mythtv setup.
I was very confused with lirc (still am on occasions!) but the controlling files with 12.04 are:

1.  /etc/lirc/hardware.conf  tells lirc where to find the IR receiver.
2.  /etc/lirc/lirc.conf      tells lirc about the timing of the pulses and gives the keypress names (eg KEY_UP)       
         to a particular train of pulses.
3.  ~/.mythtv/lircrc is a translation table between those keypress names and which key to be put into which system (eg myth)
4.  The keybindings (frontend setup) define which keys do what in any state.

You may need to chase down a trail of links or 'include' statements with these files.
Use irw to find the keypress names.  Quit with ^C

hth
Phil

I had set it up to NOT use a remote and it still recognized it.  A list of packages showed that lirc was not installed.

However, how that you have shown me the conf files needed, I am sure that I can work it out.  I'll get back once with configs once everything is working.

Thanks!

---

### Post by Dave_Alverson on 2014-03-13
If your remotes driver uses the rc subsystem, you can run with or without lirc.  Without lirc, you can use ir-keytable to change the mapping of what codes are produced by what buttons.  If you use lirc, then you let the remote generate standardized key codes, and use lirc to map those codes to the right keystrokes for each application.  I have a similar Rosewill IR receiver and I use it with devinput into lirc.

---


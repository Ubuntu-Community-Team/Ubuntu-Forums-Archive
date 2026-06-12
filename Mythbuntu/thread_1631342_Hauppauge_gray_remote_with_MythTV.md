---
title: "Hauppauge gray remote with MythTV"
date: 2010-11-26
forum: Mythbuntu
---

### Post by davidstoll on 2010-11-26
I've been searching high and low and just can't find a method for easily getting my Hauppauge IR remote working with MythTV.

I believe it is often referred to as the 350 remote.
[http://techgage.com/reviews/hauppauge/wintv_pvr350/hauppauge_350_8_thumb.jpg](http://techgage.com/reviews/hauppauge/wintv_pvr350/hauppauge_350_8_thumb.jpg)

I'm not sure which remote to select in the control center.  I've tried the Microsoft MCE and all the Hauppauge remote entries.

I've also tried the irw command, but nothing happens when I press buttons...unlike other remotes.

My IR receiver is the Microsoft transmitter/receiver.  I assume it is compatible...?

I would appreciate any help.

---

### Post by ian dobson on 2010-11-26
Hi,

I use a hauppage remote one my frontend and it works very well, using a serial/home brew serial reciever.

I are you use the reciever actually works correctly. I could well be that the reciever isn't being seen my linux. Do you have a different remote that you can test.

Have you tried replacing the batteries on the remote. Mine died just after an upgrade and after trying every possible software solution I replaced the batteries and everything worked again.

Regards
Ian Dobson

---

### Post by wyliecoyoteuk on 2010-11-26
Works fine for me, but I am using the Hauppuage TV card and receiver.

[http://ubuntuforums.org/showthread.php?t=1140411](http://ubuntuforums.org/showthread.php?t=1140411)

---

### Post by davidstoll on 2010-11-26
> **ian dobson said:**
> Hi,

I use a hauppage remote one my frontend and it works very well, using a serial/home brew serial reciever.

I are you use the reciever actually works correctly. I could well be that the reciever isn't being seen my linux. Do you have a different remote that you can test.

Have you tried replacing the batteries on the remote. Mine died just after an upgrade and after trying every possible software solution I replaced the batteries and everything worked again.

Regards
Ian Dobson

Another Microsoft MCE remote does work.  In fact, when I press a button on the Hauppauge remote, I can see the IR receiver light blink.

---

### Post by davidstoll on 2010-11-26
> **wyliecoyoteuk said:**
> Works fine for me, but I am using the Hauppuage TV card and receiver.

[http://ubuntuforums.org/showthread.php?t=1140411](http://ubuntuforums.org/showthread.php?t=1140411)

This seems to be getting a tuner card working.  I only want to make the remote usable to navigate MythTV via lirc.

---

### Post by ian dobson on 2010-11-26
Hi,

OK, if that's the case then maybe you just need to manually the lirc configuration file:-

edit file file  /etc/lirc/lircd.conf and make sure the correct hardware is included, in my conf file I have 
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

After a reboot check if irw sees anything.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-11-26
> **ian dobson said:**
> Hi,

OK, if that's the case then maybe you just need to manually the lirc configuration file:-

edit file file  /etc/lirc/lircd.conf and make sure the correct hardware is included, in my conf file I have 
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

After a reboot check if irw sees anything.

Regards
Ian Dobson

/etc/lirc/lircd.conf
is automatically updated with whatever I choose in the mythtv control panel.  The problem is I don't know which one is correct...if any...?

I'm not sure which conf file you are referring to in your second part.

---

### Post by ian dobson on 2010-11-27
Hi,

In the /etc/lirc/lircd.conf the last line is include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

Just try manually editing the lircd.conf so that it includes the line:-
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

then reboot and see of the remote works (without starting control panel). I'd imagine the remote you have is a Hauppage_350, but any hauppage should produce some key presses (up/down/ok)

Regards
Ian Dobson

---

### Post by davidstoll on 2010-11-27
> **ian dobson said:**
> Hi,

In the /etc/lirc/lircd.conf the last line is include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

Just try manually editing the lircd.conf so that it includes the line:-
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

then reboot and see of the remote works (without starting control panel). I'd imagine the remote you have is a Hauppage_350, but any hauppage should produce some key presses (up/down/ok)

Regards
Ian Dobson


It does have the "include" line above.  When I run irw, none of the key presses do anything.  :(

---

### Post by ian dobson on 2010-11-27
Hmm strange,

What do you see when you run mode2 or irrecord or  cat /dev/lirc0 and press afew buttons on the remote.

Can you attach a dump of your dmesg, maybe your ir reciever is being seen as a keyboard device.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-11-27
Actually, I didn't check the box that said "create button mappings".  I went back, changed to another random remote, saved that, then changed back to a Hauppauge remote and had it create the mappings.  Now it works.

The only thing now is that it doesn't control XBMC or Boxee.

Any ideas with those?  This is most likely not a Hauppauge problem, but more of a 10.10 issue I think.

---

### Post by davidstoll on 2010-11-28
Clarification:

The remote will work on my frontend machine that has a streamzap IR receiver.  However, it will not work with my backend/frontend machine that has a Microsoft receiver/transmitter.

hmmm

Is it not compatible with certain receivers?
The little red light blinks, but I get nothing with irw.

---

### Post by ian dobson on 2010-11-28
> **davidstoll said:**
> Clarification:

The remote will work on my frontend machine that has a streamzap IR receiver.  However, it will not work with my backend/frontend machine that has a Microsoft receiver/transmitter.

hmmm

Is it not compatible with certain receivers?
The little red light blinks, but I get nothing with irw.

The hauppage remote sends Philips RC5 codes, so just check what you Microsoft receiver supports.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-11-28
> **ian dobson said:**
> The hauppage remote sends Philips RC5 codes, so just check what you Microsoft receiver supports.

Regards
Ian Dobson

How do I do that?  I don't see any markings on it at all.  Only a serial number.  I know it's a Microsoft transmitter/receiver because it came with an RC6 MCE remote.

---

### Post by ian dobson on 2010-11-28
Hi,

OK so you know your remote is a "RC6 MCE remote" and the haupage is a RC5 reciever, so they aren't compatible.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-11-28
> **ian dobson said:**
> Hi,

OK so you know your remote is a "RC6 MCE remote" and the haupage is a RC5 reciever, so they aren't compatible.

Regards
Ian Dobson

Well the MCE remote (and I assume the receiver/transmitter) are RC6 and the Hauppauge remote (no receiver) is an RC5.

So, an RC6 receiver will not accept RC5 remotes...I take it?

Hmmm, ok, it's just strange that the RC6 receiver blinks when I hit the buttons on the RC5 remote.

---

### Post by ian dobson on 2010-11-28
> **davidstoll said:**
> Well the MCE remote (and I assume the receiver/transmitter) are RC6 and the Hauppauge remote (no receiver) is an RC5.

So, an RC6 receiver will not accept RC5 remotes...I take it?

Hmmm, ok, it's just strange that the RC6 receiver blinks when I hit the buttons on the RC5 remote.

Hi,

No it's not strange. The receiver blinks whenever it sees a IR pulse, it's just that the backend cannot process the pulse into anything worth while. It's just like when you try and read a language you don't understand, you can see then characters but you don't know what they mean.

Regards
Ian Dobson

---

### Post by the_pod on 2010-11-30
fwiw, I have that remote and it works with the Hauppauge 1100 lirc setup from the Mythtv Control Centre in all versions of Mythbuntu thru 10.4.  It is worthless at 10.10 due to tremendous latency.  I've regressed to 10.4 to avoid more hours of trouble shooting.

---

### Post by davidstoll on 2010-11-30
> **the_pod said:**
> fwiw, I have that remote and it works with the Hauppauge 1100 lirc setup from the Mythtv Control Centre in all versions of Mythbuntu thru 10.4.  It is worthless at 10.10 due to tremendous latency.  I've regressed to 10.4 to avoid more hours of trouble shooting.


What has happened to LIRC (including Streamzap) in 10.10 is really frustrating.  I wish I could revert to 10.4, but it just isn't doable.  I have too much customized and it would be way to time consuming to reformat and install fresh.

So, are we sure that a receiver that came with an IR6 remote won't accept IR5 remote signals or are we assuming?  I could very easily have another issue or be doing something else wrong.   wow, I wish I never went to 10.10.

---

### Post by davidstoll on 2010-12-01
Here is the other thing.  It won't control XBMC or Boxee.  Does anybody know how to get those to function with the "new" LIRC setup in 10.10?

It seems to be quite a mess.

---


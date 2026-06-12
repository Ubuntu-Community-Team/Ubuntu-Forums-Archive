---
title: "Sound card not detected?"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by Navyblue on 2005-11-02
When I boot up KDE it says:


> 
Informational - artsmessage

Sound server informational message:

Error while initializing the sound driver.

device: default can't be opened for playbacl (Nosuch file or directory)

The sound server will continue. using the null output device.


Is my sound card not detected? I am running Kubuntu Breezy on a Dell XPS R400 with onboard sound card (I think it is Crystal Sound CSxxxx).

What can I do?

Thanks. :)

---

### Post by Navyblue on 2005-11-02
In Debian, I need to invoke alsaconf and ask it to scan for ISA sound card. By default, it expect this card at to reside at PCI slot.

So how do I invoke alsaconf in Ubuntu? What is the package that contains it?

Thanks. :)

---

### Post by Navyblue on 2005-11-03
No one knows how to ask Ubuntu to scan for ISA sound card?

No one knows what is the alsaconf equivalent in Ubuntu?

---

### Post by noctambulo on 2005-11-03
Hi, I don't think I'm going to be much help since I face a similar problem (see my message re my ensoniq pci card). I do know that for some reason ubuntu has no alsaconf command.... Try looking at the linux sound how to since it has a lot of info on sound from isa sound cards. Good luck

---

### Post by Navyblue on 2005-11-03
Thanks. :)

I am now trying to compile the "original" alsa-utils which comes with alsaconf, hopefully it will work.

---

### Post by Navyblue on 2005-11-04
I have used Debian unstable repository to install alsa-utils and now I have alsaconf.

However, after the system detected the card, there is still no sound. alsamixer and Kmixer are working and not muted, and they can detect the sound card. But there is no sound.

What can I do here?

---

### Post by REInvestor on 2005-11-04
Facing a similar problem on a thinkpad 600.  What did you put in synaptic to get the Debian unstable repository?  I was trying to do the same thing myself.

As for your problem, do you have a manual volume control for your hardware?  On the thinkpad, I hit Fn, PgUp to adjust the volume and it beeps louder each time.  I know it may be a stupid suggestion, but are you sure the hardware volume is turned on?  Also, when was the last time you had sound on your system?

---

### Post by Navyblue on 2005-11-04
Hi there,

You can pick one repository mirror that is closest (or rather the fastest) to you from this list:

[http://www.debian.org/mirror/list](http://www.debian.org/mirror/list)

My sound card now works perfectly. It didn't work just because of a faulty audio cable :). Just for the reference, I have solved my problem by doing this:

- sudo apt-get install modconf alsa-utils

- sudo modconf

- Scroll down he list and look for your hardware of interest and enable it. (enabled items are marked with a "+") ISA sound card are listed under the /kernel/snd/isa section, and my card is listed as cs423x.
(this step is done to ask the system to "remember" the setting, I don't know if it is supposed to be this way but "alsactl store" doesn't remember the settings for me and I need to probe for the card everytime the system starts)

- exit

- sudo alsaconf
(autodection would probably not worked well, you might want to ask it to detect ISA sound cards)

- alsactl store (I am not sure if this is of any use)

Good luck. :)

---

### Post by pneaveill on 2006-08-01
Mine says this after folowing your directions. What did I miss?

FATAL: Error inserting snd_cs4231 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4231.ko): No such device

---

### Post by gotaserena on 2006-08-02
Hi pneaveill, your problem may be that the sound card is deactivated by default. If you turned apci off during boot (which is the default behaviour for machines pre 2000), you can see the status of the ISA devices by typing `lspnp -v`. Find your sound card and turn it on with `setpnp XX on` where "XX" is the number of your sound card as listed by lspnp. Try then to insert the ALSA module. If this works, you will still need to have this done automatically at boot so that the module can work.

---

### Post by pneaveill on 2006-08-02
> **gotaserena said:**
> Hi pneaveill, your problem may be that the sound card is deactivated by default. If you turned apci off during boot (which is the default behaviour for machines pre 2000), you can see the status of the ISA devices by typing `lspnp -v`. Find your sound card and turn it on with `setpnp XX on` where "XX" is the number of your sound card as listed by lspnp. Try then to insert the ALSA module. If this works, you will still need to have this done automatically at boot so that the module can work.
Dumb question time: would it be easier to somehow uninstall the ISA card with a PCI or try setting this thing up?

I have a PCI creative labs card which I would prefer. But not sure how/what to do.

Another dumb question here: I typed in what you said and it responded with:
bash: lspnp: command not found

---


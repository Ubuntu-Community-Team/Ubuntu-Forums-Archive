---
title: "No sound on Compaq Deskpro EN"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by acorn22 on 2006-06-27
I just installed ubuntu right after the release of Dapper, and I haven't found a way to turn on the sound. When I click on the volume button it gives me an error saying there is no sound card. I know there is one biuld on board, but I don't know how to activate it. Where do I get the drivers? Or do I already have them?

Thanks

---

### Post by glotz on 2006-06-27
Does **aplay -l** say anything? Do you know what soundchip it uses?

---

### Post by acorn22 on 2006-06-27
```
aplay -l
```

```
aplay: device_list:221: no soundcards found...
```

I do't know the chipset. How do i find out?

---

### Post by glotz on 2006-06-28
Try **lspci -v**. You could also take a look at some manuals that came with the box or take a peek in the case.

---

### Post by acorn22 on 2006-06-30
Sorry for the delay... small family emergency

ok I typed what you said and got a bunch of output, and my linux computer has no internet acces so i can't copy and paste. I didn't see anything about sound in it though.

I looked under the hood and found this chip:
```

__________________
|ESS.............|
|Audio drive.....|
|es1869f    g648.|
|tau44623a.......|
_|4,214,125.......|_


```

so...

---

### Post by az on 2006-06-30
[QUOTE=acorn22]Where do I get the drivers? Or do I already have them?

Thanks[/QUOTE]
Although my Deskpro En is my favorite box, it is rather old.  The sound chip is on the ISA bus and the linux kernel cannot safely scan it (neither can windows, but the hardware vendors just have you install the drivers.)

You just need to tell it to load the driver on boot.

open a terminal and run

sudo gedit /etc/modules 

and add

snd-es1688
at the end of the file.  save and reboot.  You will have sound.

---

### Post by az on 2006-06-30
Also, does your box power off?  I have to add acpi=force for it to shutdown and poweroff.

add that to the stanza in /etc/grub/menu.list and run

sudo update-grub


## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=force


Again, it's because the bios is pre-2000 and that year is the cutoff for linux to use acpi.  Otherwise it should be able to poweroff using apm, but it is a bug in the Dapper kernel - it worked fine with the other previous releases.

---

### Post by acorn22 on 2006-07-01
I will try the sound thing. But as for power, I love this box :D I can press the power button once and it hibernates, I hold it for 3 seconds and it shuts down. When I hit shut down in linux, it does not power down though, just stops at "will now halt" Is that what api=force whatever for then?

---

### Post by acorn22 on 2006-07-02
Alright, some problems.

I did what you told me with gedit, and the file is empty. Then I went in with finder or whatever it's called (still used to mac) and I didn't see and modules folder in the /ect/ folder.

oh, And i can't save the file in gedit either because it gives me an error message

---

### Post by glotz on 2006-07-03
modules isn't a folder but a file. What error do you get when trying to save it? Read only? Did you **gksudo gedit /etc/modules** and paste in *snd-es1688*?

---

### Post by acorn22 on 2006-07-03
[quote=glotz]What error do you get when trying to save it?[/quote]

```
Could ot save
unexpected error: File not found
```

[quote=glotz]Did you **gksudo gedit /etc/modules** and paste in *snd-es1688*?[/quote]

no, I used "sudo.."

I also now tried "gksudo..."

once again the file is empty, and in the terminal window it says a bunch of stuff before opening gedit. Almost every line has the word failed or error or something. I can't just copy paste since is has no internet :(

---

### Post by acorn22 on 2006-07-03
As it turns out, I am dumber than shit. 

I spelled etc as ect. I always do that! :oops:

But, the quality sucks. It is very static-y. I will test the headphones to see if it's them.

---

### Post by glotz on 2006-07-03
:) (that's why you always copy/paste when possible and TAB autocomplete when not)
Does it have multiple outs, (speaker out and line out, etc), one will give better quality than others probably. Also, try killing mics and other rec sources, unless you really use them. They can give you static. Also, many onboard cards get electric interference straigt from the mobo itself or the power source. There's not much you can do about it, as far as I know. Some electricians will surely disagree however.

---

### Post by az on 2006-07-03
[QUOTE=glotz]:) Also, try killing mics and other rec sources, unless you really use them. They can give you static. [/QUOTE]

I'll try that.  I have a usb wireless adapter that really makes a lot of noise come from the speaker when it is used.

---

### Post by glotz on 2006-07-03
whoa, collateral damage! ;)

---

### Post by glotz on 2006-07-03
I think that's another issue, radio interference, but I guess it can't hurt to try. One thing you could try is shielding the speakers with aluminium foil. See [theory](http://en.wikipedia.org/wiki/Faraday_cage) and [images](http://freespace.virgin.net/michael.tucknott/faraday_cage_page.htm).

---

### Post by acorn22 on 2006-07-04
Yeah, I found one to be much clearer. The other seemed to get static only when the processor was making that weid processor sound that I have no idea how to describe. The other one was a bit quieter though. That is ok since I am using headphones and unlike most 16 year olds, I value my eardums ;)

---


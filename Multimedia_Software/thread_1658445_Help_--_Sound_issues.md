---
title: "Help -- Sound issues"
date: 2011-01-02
forum: Multimedia Software
---

### Post by JMatthewman on 2011-01-02
I have just installed Ubuntu 10.10 but am having some issues with onboard sound devices on my Asus P7P55D motherboard.

The sound preferences window shows:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179937&stc=1&d=1294003943[/IMG]
'Internal audio' with 1 Output / 1 input (which I presume is my front headphone and mic ports so is set to 'Analogue stereo duplex'
and
'Juniper HDMI Audio [Radeon HD 5700 Series]' (which would obviously appear to be the HDMI output on my graphics card)

but I can find no controls or details for the 6 audio ports on the rear board or the S/PDIF optical output at the back(which I'm not too bothered about at the moment).

If I set the 'Internal audio' to 'Analogue Headphones' in the output tab the front headphone jack is a suitable volume. However if it is set to 'Analogue output' the rear speaker out outputs (and the headphone jack is very loud).

In summary, the control for my front headphone out is affecting my rear speaker outputs, and the rear speak outputs are not recognized or properly controllable, does anybody have any ideas? (sorry if that was a bit rambling)

[RIGHT]Thanks,
Joel
[/RIGHT]

---

### Post by kostkon on 2011-01-02
The *gnome-alsamixer* utility will give you access to your "hardware" volume levels and switches.

---

### Post by lidex on 2011-01-02
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-digout 
```
Save. Close. Reboot.

---

### Post by JMatthewman on 2011-01-03
Thanks for the fast responses.

How do I open the gnome-alsamixer utility if that is not the same as the sound preferences window I included a screenshot of? Will I need to install it or is it pre-installed as part of the base package?

And what should the entry in the alsa-base have done? as after inserting it at the end, saving and restarting I can see no change whatsoever in the sound preferences window, and as I said above I do not know how to access/use the alsa utilities this file seems to control.

[B]EDIT:

[/B]Gnome Alsa-mixer installed and working! Thankyou both for your help!

My front mic and headphone are now showing as part of the main sound card, is there a way to manually separate them?/generally tidy up the interfaces/channel list? and is there any way to have this replace or work with the built-in sound preferences so I can open the settings from the sound icon in the taskbar?

[RIGHT]Thanks,
Joel
[/RIGHT]

---

### Post by lidex on 2011-01-03
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---


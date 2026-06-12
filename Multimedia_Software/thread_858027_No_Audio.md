---
title: "No Audio"
date: 2008-07-13
forum: Multimedia Software
---

### Post by MNICY on 2008-07-13
Hello everyone.
I just installed Kubuntu 8.04 today, and everything is going good except I have one problem.

No audio at all.
None :(

I checked kmix, and nothing is muted.
I am using ALSA.

The annoying thing is that sound worked great in Ubuntu 8.04(which i had previously). If it was a problem with my hardware, then I would be fine.. but you know... I'm a bit annoyed that it stops working in Kubuntu :(

I did a new installation of Kubuntu over the partition were my Ubuntu was; so its not like I typed "sudo apt-get install kubuntu-desktop"; if that is what you are thinking the problem might be.
But I also kept all the files on my /home; because i set that as a separate partition. I dont know if this would cause the problem or not, but I just cant figure out what is wrong.

Any help is appreciated.
-MNICY

EDIT:
Oh yes, it is 64bit version of Kubuntu.

---

### Post by cotcot on 2008-07-13
I had this a couple of times with an upgrade. Deleting .asoundrc and .asoundrc.asoundconf solved the problem. 
If you try it do it by changing the file name instead of delete it : 

```
mv .asoundrc .asoundrc_old
mv .asoundrc.asoundconf .asoundrc.asoundconf.old
sudo mv /etc/asound.conf /etc/asound.conf.old
```

---

### Post by MNICY on 2008-07-13
> **cotcot said:**
> I had this a couple of times with an upgrade. Deleting .asoundrc and .asoundrc.asoundconf solved the problem. 
If you try it do it by changing the file name instead of delete it : 

```
mv .asoundrc .asoundrc_old
mv .asoundrc.asoundconf .asoundrc.asoundconf.old
sudo mv /etc/asound.conf /etc/asound.conf.old
```

were are thoes files located? It says "no such file or directory"

---

### Post by crtlbreak on 2008-07-13
i think you are referring to the gui viewer called nautilus
those folders will be in your home folder - if you cant seem them you need to CNTRL+H to show "hidden files" when you are browsing through nautilus (gui file manager)

the best way is not to use the gui but (as cotcot has shown) use the terminal window to effect this.

regards
crtlbreak

---

### Post by MNICY on 2008-07-13
No, they are not in my home folder, even when I select "show hidden files"

---

### Post by cotcot on 2008-07-13
Look in /etc
It is possible that you do not have them. (I do not have them)

---

### Post by crtlbreak on 2008-07-14
neither - but they should be in the users home folder such as 
/user/.asoundrc

:rolleyes: 
But a good place to start with sound diagnosis is [here]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28configure%29%7C%28soundcard%29%7C%28howto%29")   - let me know how you come along.
regards

---

### Post by MNICY on 2008-07-14
could not find them in /etc either
> **crtlbreak said:**
> neither - but they should be in the users home folder such as 
/user/.asoundrc

:rolleyes: 
But a good place to start with sound diagnosis is [here]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28configure%29%7C%28soundcard%29%7C%28howto%29")   - let me know how you come along.
regards
nope, they are deffenlty not in my home folder :(
Anyway, using that page, I tried two things. Both are dead ends it looks like to me. Here they are. There is more on the page, but I dont know what to try :-\

find /lib/modules/`uname -r` | grep snd
```
/lib/modules/2.6.24-16-generic/ubuntu/snd-bt-sco.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/soc/snd-soc-core.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-mtpav.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-aloop.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-dummy.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-virmidi.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-serial-u16550.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-portman2x4.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/snd-mts64.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-rawmidi.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-rtctimer.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-dummy.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-device.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-virmidi.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-page-alloc.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/snd-cs8427.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/snd-i2c.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4114.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/other/snd-pt2258.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/i2c/other/snd-ak4117.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/synth/snd-util-mem.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-cs5530.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp-modem.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-als300.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/trident/snd-trident.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/pdplus/snd-pdplus.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/mixart/snd-mixart.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-bt87x.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0m.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-rme32.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-rme96.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/nm256/snd-nm256.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/vx222/snd-vx222.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-cs4281.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/riptide/snd-riptide.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-ad1889.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-ens1370.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-azt3328.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-es1938.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-cmipci.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx-modem.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-maestro3.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-via82xx.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-es1968.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-ens1371.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-als4000.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-fm801.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/snd-sonicvibes.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/usb/snd-usb-lib.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/usb/snd-usb-audio.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb-common.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pcmcia/pdaudiocf/snd-pdaudiocf.ko

```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by sypherz on 2008-07-14
I recently installed Ubuntu 8.04 and the sound wouldn't work, I tried everything i could think of and nothing worked until i tried this

open a terminal and edit modprobe.conf, This may not exist which is ok, once you type this command it will be created

Type:sudo vim /etc/modprobe.conf

Within this file add the line
Type: options snd-hda-intel model=lenovo

Now hit "Shift :" and type "wq". For those of you who doesn't know what this does it will write the file and then quit

Now simply reboot and you should have sound

Im not saying this will work for you but it did work for me

If this doesnt work you might want to try to update your ALSA drivers

---

### Post by sypherz on 2008-07-14
Within this file add the line
Type: options snd-hda-intel model=lenovo

I forgot to add to change lenovo to the model of computer you have

---

### Post by Zelow on 2008-07-14
Ok so to begin I am sort of new to Linux and Ubuntu at that.  I am using Ubuntu 8.04 (hardy I think)  My sound is work for .mp3 files but I get no sound from youtube.com Does anyone have a suggestion why this would be?

---

### Post by MNICY on 2008-07-14
sypherz:
nope, still no sound :(

---

### Post by MNICY on 2008-07-15
forget it guys :(
I give up. Back to GNOME for me.

You know, all these KDE people talk about how great it is.. and I agree. I like how KDE feels.
But i have never had any luck with it at all. 

Places were GNOME works fine, KDE fails. It is probably because I dont have an excessive knowledge about linux (just the basics from using it as my primary desktop for over a year now)

I will try Kubuntu again when the next Ubuntu is released. Hopefully it works better for me then.

---

### Post by crtlbreak on 2008-07-15
> **sypherz said:**
> Within this file add the line
Type: options snd-hda-intel model=lenovo

I forgot to add to change lenovo to the model of computer you have

I dont think MNICY should be editing his .conf file to refer to an 
intel card when the chipset is an ALC883 (i think it is a realtek?) and his seems like a desktop when your help refers to a laptop it seems?

Like saying yes - this bmw cylinder head should fit my toyota  - as they are both 3litre engines? :confused:  :grin: :grin: :grin:

---

### Post by crtlbreak on 2008-07-15
> **Zelow said:**
>  .....  but I get no sound from youtube.com Does anyone have a suggestion why this would be?

zelow - Youtube needs flashplayer installed - the standard flashplayer in the repositories does not work for all flash files.
try  the adobe flash player at 
[http://www.adobe.com/downloads/]("http://www.adobe.com/downloads/") and select linux (obviously) then download to a location  - depending where you have customised your download options in firefox.
then install with standard debi installer package.
let me know if this solves the issue.
regards.

---

### Post by gehentogo on 2008-08-21
I am having the same problem with YouTube.  Weird thing is, it used to work.  Now it doesn't.  When I install Flash, I get this:
> 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

Any help for us 64 bit users?

---


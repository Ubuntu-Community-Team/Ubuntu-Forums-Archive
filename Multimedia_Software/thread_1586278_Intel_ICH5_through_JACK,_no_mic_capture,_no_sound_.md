---
title: "Intel ICH5 through JACK, no mic capture, no sound on video players"
date: 2010-10-01
forum: Multimedia Software
---

### Post by EpicFai1 on 2010-10-01
Here we go, for audio and video and stats:

log@EPICFAIL:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17
 1 [U0x46d0x807    ]: USB-Audio - USB Device 0x46d:0x807
                      USB Device 0x46d:0x807 at usb-0000:00:1d.7-4, high spee
log@EPICFAIL:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_audio
log@EPICFAIL:~$ cat /proc/asound/card0/codec#0 |grep -i codec
cat: /proc/asound/card0/codec#0: No such file or directory

--I am trying to get the audio/video programs through Ubuntu Studio Control to work with my Logitech cam/mic through a USB port. It reads the camera in some programs, I have JACK working but cannot find a usable video/audio combo program to work for me, or to use my Logitech. 
--assist please

---

### Post by Pablo_F on 2010-10-01
Hi, 

First of all, you have to configure jack to use your usb card which is your webcaam/micro, no? See the interface field and choose the snd_usb audio, not the intel. Sorry if I mislead you before.

Once that, hopefully, you have jack up and running with you usb audio card, note that you will be able to capture or playback only with programs that are jack-aware. 

For example, you can install from synaptic "vlc" and "vlc-plugin-jack".

In VLC, Tools->Preferences->Audio, choose Jack output.

If you wish that the outs auto-connect to the system playbacks (audio card's outs), edit:

gedit ~/.config/vlc/vlcrc

Search for these lines:

# Automatically connect to writable clients (boolean)
#jack-auto-connect=0

Change the second line to:
jack-auto-connect=1

Once the jack server is up and running, only jackfied apps will have sound and they will have sound through the interface (the audio card) you chose in qjackctl setup. You connect clients' ports by means of the connect window of qjackctl (Jack Control). System: playbacks represents the outputs, system: captures the inputs.

If in doubt, paste the contents of the message window of qjacktl, the output of "aplay -l"
and the output of "lsusb", with your usb device connected, of course.

Cheers! Pablo

---


---
title: "tvtime on PC using comcast cable"
date: 2011-05-03
forum: Multimedia Software
---

### Post by bean1945 on 2011-05-03
I would like to try tvtime on my Dell PC, bu I do not understand how to use the encrypted signal from comcast cable. I realize I will need to purchase a tv capture card. What is the best one for a Intel Core I3? Is there a USB version that will work?

My TV is hooked to a TIVO HD box that has a comcast cable card. Is the signal decrypted by the cable card and then is it just necessary to obtain the decrypted signal from the TIVO output?

---

### Post by wolfen69 on 2011-05-03
I have my Cablevision box output hooked into my TV card directly. Just change the channel on the card to ch. 3 and change channels on the box or TIVO. 

I use a Hauppauge PVR150 tv card (PCI). If you get that one, (you'll have to search around online) [here]("http://ubuntuforums.org/showthread.php?t=1734916") is my tutorial to get it working. 

Good luck if you get a different card, as tv tuners can be a pain in the butt to get working in linux.

---

### Post by bean1945 on 2011-05-03
Wolfen,

Thanks for your suggestion for a capture card and the pointer to your tutorial!

Jerry

---

### Post by merkez3110 on 2011-05-20
[FONT=Lucida Console]my hardware first: saa7134 / alsa650
to run it with tvtime (with sound, etc.)
  
don't forget to "reboot" when you're told so.
  
(1)
insert [/FONT][FONT=Lucida Console]"saa7134"[/FONT][FONT=Lucida Console] at the end of file "/etc/modules"
  
(2)
insert [/FONT][FONT=Lucida Console]"options saa7134 i2c_scan=1 card=81 tuner=54" into [/FONT][FONT=Lucida Console]"/etc/modprobe.d/options" file
  
reboot
  
(3)
$ sudo apt-get install sox libsox-fmt-all tvtime xmltv-util
  
(4)
$ sudo apt-get install tvtime
tv standart > PAL
sound standart > PAL-BG
frequency table > europe
  
(5)
$ lspci | grep SAA
will give output like as follows:
02:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
"02:03.0" is the address of the sound system (select yours from your output)
  
(6)
$ LANG=C pactl list | grep -A2 alsa
note all output lines like "alsa_input.pciXXXXXXXXXXXXXXX"
for example:
alsa_input.pci-0000_02_03.0.analog-stereo
alsa_output.pci-0000_00_10.1.analog-stereo.monitor
alsa_input.pci-0000_00_10.1.analog-stereo
select the one with the matching numbers noted in step 5
for example, my selection would be: "alsa_input.pci-0000_02_03.0.analog-stereo"
  
(7)
insert the line
[/FONT][FONT=Lucida Console]"load-module module-loopback source=alsa_input.pci-0000_02_03.0.analog-stereo"
at the end of file [/FONT][FONT=Lucida Console]"/etc/pulse/default.pa"
  
(8)
restart pulse audio
$ pulseaudio -k
  
or better reboot
  
(9)
now correct the line
[/FONT][FONT=Lucida Console]<option name="MixerDevice" value="default/Line"/>[/FONT]
in the file  [FONT=Lucida Console]"/etc/tvtime/tvtime.xml"
like:
<option name="MixerDevice" value="hw:0/PCM"/>
  
reboot.
  
start tvtime (no need to use "sudo", use the gui menu)
  
search the channels and you're done.
  
any questions? [email]merkez3110@gmail.com[/email]
[/FONT]

---


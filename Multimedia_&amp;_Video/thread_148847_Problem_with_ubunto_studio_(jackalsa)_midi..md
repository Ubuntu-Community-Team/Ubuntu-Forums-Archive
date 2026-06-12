---
title: "Problem with ubunto studio (jack/alsa) midi."
date: 2006-03-22
forum: Multimedia &amp; Video
---

### Post by bwanab on 2006-03-22
When I start jack (using qjackctl), I get the following:

----------
20:15:51.472 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
----------

Sure enough, when I start qsynth for example and vkeybd, then go to connect them in qjackctl, they are not listed as midi devices. 

I understand that I have no midi hardware currently, but the two applications mentioned are software only midi. It seems like they should be recognized. If I had a midi adaptor, would my outcome be different (i.e. would the alsa sequencer be happy), or would I get the same problem? Assuming the latter, does anybody know what might be the problem?

---

### Post by dolson on 2006-03-22
Did you sudo modprobe snd-seq?

[http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer)

---

### Post by bwanab on 2006-03-23
[QUOTE=dolson]Did you sudo modprobe snd-seq?

[http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer)[/QUOTE]

No, that is probably the problem. I'll give it a try. Thanks for the pointer.

---

### Post by Coburn on 2007-02-03
> **bwanab said:**
> No, that is probably the problem. I'll give it a try. Thanks for the pointer.

I tried it and VirtualKeyboard is still silent.

---

### Post by sgx on 2007-02-03
> **Coburn said:**
> I tried it and VirtualKeyboard is still silent.
you must load a soundfont in fluidsynth/qsynth to hear anything. Try with zynaddsubfx
or amsynth, or download a soundfont(s) from [www.hammersound.net](www.hammersound.net) in the 
Soundfonts by Thomas section, make a folder called asf2 in /home/you for them, and select
one from qsynth/fluidsynth panel/menu...
run
jackd -d alsa -r 44100
qjackctl
zynaddsubfx
vkeybd
in midi panel of qjack, connect vkeybd to zynaddsubfx
in audio panell of qjack, connect zynaddsubfx to alsa_pcm
(zyn has its own vkeys on a panel button)
all these must run as the -same- user, no mix/match allowed.
make sure rates like 44100 are the same in all the interfaces/config files

run command lsmod...do you really have snd_seq in the list? If you modprobe it, you may still have
to create textfile /etc/module and type snd_seq and save it to survive rebooting. Give it a try!

---


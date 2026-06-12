---
title: "Very silent audio from headphones slot"
date: 2015-02-22
forum: Multimedia Software
---

### Post by fos4 on 2015-02-22
Hi,
I have big problem with sound on my laptop **Toshiba Satellite P200-17C**. I'm using elementary OS distribution (Ubuntu 14.04). 
On laptop speakers sound works fine, but after plug in headphones I can't hear anything. I tried plug in Amplifier to headphones slot, and then on very high volume there are some sounds.
I've checked on other distribution (by live-cd) and all works fine.
What I did:
- Changing all switches and levels in alsamixer
- Reinstaling alsa and pulseaudio packages

PS My target is to plug in amplifier, not headphones. Maybe can I use other slot? I was tried on other slots, but with no effect.

Please help.
This is my alsa config:
[URL="http://www.alsa-project.org/db/?f=c2919c65daaf389cc7d2df72bfedae6bb6632fa0"]http://www.alsa-project.org/db/?f=c2919c65daaf389cc7d2df72bfedae6bb6632fa0

[/URL]

---

### Post by Yellow Pasque on 2015-02-23
[https://github.com/torvalds/linux/commit/cb766404e6b8c566569eb9ada02ea45d28729864](https://github.com/torvalds/linux/commit/cb766404e6b8c566569eb9ada02ea45d28729864)
[https://bugzilla.novell.com/show_bug.cgi?id=569991#c34](https://bugzilla.novell.com/show_bug.cgi?id=569991#c34)

As suggested in above links, try this:
```
sudo apt-get install alsa-tools
sudo hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD 0x00
```

If it works, I believe you can make it permanent like so:
```
echo "options snd-hda-intel model=hp-eapd" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

### Post by fos4 on 2015-02-23
Thanks a lot for your response.

I've read those comments from links and all looks similar. But _solution doesn't work_. Maybe the point is that I can hear sound but very silent, system isn't completly muted.

---

### Post by Andra on 2015-02-25
I had recently a very similar problem, maybe my solution may help:
at first I changed [Element Speaker] part in
/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf

which was:
switch = off
volume = off

and now is:
switch = on
volume = ignore

after reboot I changed "Output volume" (near 100%) in Sound Settings, and now it's ok.

Sorry, if it's of no help, I'm not a great specialist in sound things and I have Ubuntu 12.04.

---

### Post by fos4 on 2015-02-27
Thank you Andra but your solution doesn't work for me.

I found working solution:

author: colhathi


[LIST=1]
[*]Download the basic run.py script to your preferred download folder by following the instructions on [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer) i.e. run the following command in a terminal wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
[*]Check that the permissions of run.py are set to root by using sudo chown root:root /<download location>/run.py
[*]In a terminal change run.py to an executable file using sudo chmod +x /<download location>/run.py
[*]Run the script in a terminal sudo python run.py
[*]In the left-hand sidebar select Node[0x15] PIN
[*]Check the box next to EAPD
[*]Click Exp then save as 'snd_hda_codec_diff.py' in /etc
[*]Add "python /etc/snd_hda_codec_diff.py" without the quotes to the  file /etc/rc.local just above the line "exit 0" with your favourite  editor
[/LIST]
  After the next reboot your headphones should work.

---


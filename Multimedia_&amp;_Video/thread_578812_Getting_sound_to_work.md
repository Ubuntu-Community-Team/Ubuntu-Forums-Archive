---
title: "Getting sound to work"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by Maxcore on 2007-10-17
Hi, I just started using Ubuntu and currently my sound does not work. No sound comes out for any application. I think it may be a driver problem because I am not sure if it is installed or not but I do not know what my sound card is. Any help would be greatly appreciated.

---

### Post by montres on 2007-10-17
Hello and wellcome!

I had the same problem when I first installed ubuntu. I solved it by following instructions on this help page: [https://help.ubuntu.com/community/HowToSetupSoundCards]("https://help.ubuntu.com/community/HowToSetupSoundCards")

 I hope it proves helpfull!

---

### Post by Maxcore on 2007-10-17
Hmm I have read this an I am still lost as to what to do. My card name is CS46xx and i cannot figure out how to fix this sound!

---

### Post by montres on 2007-10-17
try the following

Open a terminal and type this command:
```
sudo modprobe snd-cs4236
```

enter your password when prompted

After that type this command:
```
alsamixer
```

Use the sliders to turn the volume up and try playing an mp3 or something to see if it works

You can open a terminal at:
Applications menu -> Accessories -> Terminal.

tell me if it works!

---

### Post by Maxcore on 2007-10-18
It still did not work, when I do the "sudo modprobe snd-cs4236" I get this error:
> FATAL: Module snd_cs4236xx not found.


---

### Post by Maxcore on 2007-10-18
I got it working thanks to your advice, thanks so much.

---

### Post by montres on 2007-10-18
Glad I could be of help!

---

### Post by SCGreg on 2007-10-19
Having the same problem here - I didn't stick a soundcard in my system when I was making it cos I'm not a heavy sound user.. I use the onboard sound on my Asus M2N-E motherboard, anyone have any idea which sound driver I need? It's just a standard 7.1 channel surround

---


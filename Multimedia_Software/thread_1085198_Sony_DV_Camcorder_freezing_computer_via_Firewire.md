---
title: "Sony DV Camcorder freezing computer via Firewire"
date: 2009-03-02
forum: Multimedia Software
---

### Post by sol87 on 2009-03-02
I Have a Sony Digital Handycam DCR-TRV17 DV camcorder connected via firewire and when i connect it its fine but when i turn the camcorder on my computer just freezes, like it would when it crashes, but when i turn the camera off my computer just unfreezes and continues running like normal

Im very disappointed in the lack of camcorder/webcam support in ubuntu(but i still love it)

It did work perfect in windows so its not the camera or firewire port

Help?

**I have ubuntu 8.10**

---

### Post by sol87 on 2009-03-03
I dont want this to be the second time nobody helps me on these forums

BBUUMMPP

---

### Post by sol87 on 2009-03-03
~$ cd  /dev/video0
bash: cd: /dev/video0: No such file or directory


Where is my /dev/videoX at???

---

### Post by charlie1953 on 2009-08-27
I have exactly the same problem.
Anyone know the answer?
I am using Jaunty and it was working a few days ago.
Only thing I can think has changed is that I have accepted recommended updates and have installed qemu.

---

### Post by charlie1953 on 2009-08-30
Anyone got any ideas?

---

### Post by bigtom2 on 2009-09-02
use this it works with all dv cameras

Quote:
sudo apt-get install kino  

Quote:
sudo apt-get install dvgrab  

Quote:
sudo apt-get install libraw1394-8  

Quote:
sudo apt-get install libraw1394-dev  

C) Start kino in terminal at this point it pulls up the gui

Quote:
sudo kino 
 
you also need
mjpegtools

to make mp3 s out of dvs 












> **sol87 said:**
> I Have a Sony Digital Handycam DCR-TRV17 DV camcorder connected via firewire and when i connect it its fine but when i turn the camcorder on my computer just freezes, like it would when it crashes, but when i turn the camera off my computer just unfreezes and continues running like normal

Im very disappointed in the lack of camcorder/webcam support in ubuntu(but i still love it)

It did work perfect in windows so its not the camera or firewire port

Help?

**I have ubuntu 8.10**

---

### Post by charlie1953 on 2009-09-19
Thanks for your reply bigtom but unfortunately that did not help. I have already got all that stuff installed. As I said all was working fine then suddenly one day I have the problem that as soon as I plug the firewire cable into my camcorder the whole system freezes - no mouse, no keyboard not even capslock light works. Then I unplug the cable and all is ok again - no need to reboot.
Also happens if I switch on the camcorder when the cable is plugged in. Switch it off again and the system unfreezes.

I know about the need to run kino using sudo but my problem starts before I run kino - right after a fresh boot.

Can't find anyone with the same problem by searching the internet - is it just me and Sol87?

BTW mine is a Panasonic camcorder not a Sony.

---

### Post by Unterseeboot_234 on 2009-09-19
I have the original Sony DRV10xxx HandyCam, DV-firewire... if I fire up Kino and/or Cinelerra as

```
sudo kino
[password]

sudo cinelerra
[password]
```

then, I get the  << [] >> controls lit up in kino capture tab pane. I can run the Sony camera through the Kino GUI. The capture feature with cinelerra works.

kino works with another program called dvgrab if I firewire-connect my camera, turn it on, that puts raw1394 module in /dev.

```
dvgrab
or dvgrab --help
```

then is default on 'auto' to start a file to hard disc if the HandyCam is set to 'Play'. Indeed, many times I just use dvgrab as the terminal program  to do as a bulk thingy, getting clips into a computer folder. Every place you hit the pause while shooting video will starts a new video clip with a new filename.


Try those suggestions. There has to be some answer. It works for me in 64-bit Ubuntu. Buidling my own kino as /root worked for me in 32-bit Drake Ubuntu. I mention that to say it does work.

---


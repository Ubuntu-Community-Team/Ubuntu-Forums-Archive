---
title: "No Audio Output"
date: 2010-03-06
forum: Multimedia Software
---

### Post by ahl395 on 2010-03-06
Hello Everyone :)

Im somewhat new to Linux, and am having some problems with sound... :/

Under sound preferences, there is nothing listed under Hardware. And under Output, All it says is Dummy Output

Another thing to note, is that it worked when i first installed Ubuntu. after i updated, is when my sound card dissapeared from hardware and my speakers are gone from output.

Can anyone help me? Thanks so much in advance. :)

---

### Post by RedSingularity on 2010-03-06
So nothing is playing sound?  In a terminal type 

alsamixer

and make sure all the levels are up.

---

### Post by lidex on 2010-03-06
Walk through this guide:
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

Anything you don't understand, ask.

---

### Post by ahl395 on 2010-03-06
> **RedSingularity said:**
> So nothing is playing sound?  In a terminal type 

alsamixer

and make sure all the levels are up.
  Pretty much, yep. everything that looks important.

heres a screenshot 

[IMG]http://i49.tinypic.com/9sry2u.jpg[/IMG]

---

### Post by ahl395 on 2010-03-06
> **lidex said:**
> Walk through this guide:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Anything you don't understand, ask.

Ok ill try it now, thanks ^^


Ok, well im trying the first part and i do think that is my problem. It finds my card and is listed as 0 instead of 1.

but it wont let me put the file in modprobe.d ... it says_** *Error moving file: Permission denied***_
And when i try to change the folders permissions, it then says [U][B][I]You are not the owner, so you cannot change these permissions

[/I][/B][/U]What can i do? lol i am the only user on here and am the owner :p ill try continuing with the guide.

---

### Post by ahl395 on 2010-03-06
nevermind this post lol,  sry

---

### Post by lidex on 2010-03-06
> **ahl395 said:**
> Ok ill try it now, thanks ^^


Ok, well im trying the first part and i do think that is my problem. It finds my card and is listed as 0 instead of 1.

but it wont let me put the file in modprobe.d ... it says_** *Error moving file: Permission denied***_
And when i try to change the folders permissions, it then says [U][B][I]You are not the owner, so you cannot change these permissions

[/I][/B][/U]What can i do? lol i am the only user on here and am the owner :p ill try continuing with the guide.

0 is highest priority, so if your soundcard is 0, that is correct. So don't worry about that. Anything outside your home folder is not owned by you in ubuntu, by default, so you need elevated privileges to change.

---

### Post by GameOverDood on 2010-03-06
> **ahl395 said:**
> Hello Everyone :)

Im somewhat new to Linux, and am having some problems with sound... :/

Under sound preferences, there is nothing listed under Hardware. And under Output, All it says is Dummy Output

Another thing to note, is that it worked when i first installed Ubuntu. after i updated, is when my sound card dissapeared from hardware and my speakers are gone from output.

Can anyone help me? Thanks so much in advance. :)


I did encounter this a couple of times today when I did a fresh (dual boot) install of Ubuntu 9.10. However, strangely enough, it only happened if I hit the Enter button during the GRUB loader during boot-up, thus bypassing that menu prematurely and loading Ubuntu. Otherwise, if I just let the timer run out and load Ubuntu on its own then the sounds come back on and audio devices are recognized again.

If you're doing a dual-boot like I am then try my method first and see if that works. If it works, then it's a minor nuisance that I'm sure we can live with. Otherwise, there may be something else that's wrong. And if you're not doing a dual-boot setup like I am then, once again, there could be some other issue. Unfortunately at that point, I don't think I can be of much help... sorry. :(

---

### Post by ahl395 on 2010-03-06
> **lidex said:**
> 0 is highest priority, so if your soundcard is 0, that is correct. So don't worry about that. Anything outside your home folder is not owned by you in ubuntu, by default, so you need elevated privileges to change.

Okay... can you tell me how to do that exactly? lol because the guide says to do it :/ :)


> **GameOverDood said:**
> I did encounter this a couple of times today when I did a fresh (dual boot) install of Ubuntu 9.10. However, strangely enough, it only happened if I hit the Enter button during the GRUB loader during boot-up, thus bypassing that menu prematurely and loading Ubuntu. Otherwise, if I just let the timer run out and load Ubuntu on its own then the sounds come back on and audio devices are recognized again.

If you're doing a dual-boot like I am then try my method first and see if that works. If it works, then it's a minor nuisance that I'm sure we can live with. Otherwise, there may be something else that's wrong. And if you're not doing a dual-boot setup like I am then, once again, there could be some other issue. Unfortunately at that point, I don't think I can be of much help... sorry. :(

hmm, yes i am. 

ill try it! :p

Edit: Nope, no avail :/

---

### Post by lidex on 2010-03-06
I'm in lucid testing right now and haven't used karmic so I'm not sure if it's the same but look in your applications menu: "System>Preferences>Default Soundcard" and if it's there make sure proper device is chosen.

---

### Post by ahl395 on 2010-03-06
> **lidex said:**
> I'm in lucid testing right now and haven't used karmic so I'm not sure if it's the same but look in your applications menu: "System>Preferences>Default Soundcard" and if it's there make sure proper device is chosen.

Ahh, ok np 

And theres nothing having to do with my soundcard in there at all unfortunately

---

### Post by lidex on 2010-03-06
> **GameOverDood said:**
> I did encounter this a couple of times today when I did a fresh (dual boot) install of Ubuntu 9.10. However, strangely enough, it only happened if I hit the Enter button during the GRUB loader during boot-up, thus bypassing that menu prematurely and loading Ubuntu. Otherwise, if I just let the timer run out and load Ubuntu on its own then the sounds come back on and audio devices are recognized again.

If you're doing a dual-boot like I am then try my method first and see if that works. If it works, then it's a minor nuisance that I'm sure we can live with. Otherwise, there may be something else that's wrong. And if you're not doing a dual-boot setup like I am then, once again, there could be some other issue. Unfortunately at that point, I don't think I can be of much help... sorry. :(

There is a chance that you are not booting into the correct kernel if you just upgraded to karmic. To fix that, run these commands from a terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Reboot

---

### Post by lidex on 2010-03-06
If it's still not working, right click on the alsa-info script link in my sig and "save (link) as" to your user folder. Then execute this command (in a terminal - applications>accessories>terminal):
```
sudo bash utils_alsa-info.sh
```

Post the link if you choose to upload to pastebin, or post here using code tags.

---

### Post by ahl395 on 2010-03-06
Ok, well to your first post, i tried it. and it goes through and then asks me Y/n?
No matter which one i say it then says Abort after and stops. :/

By reading the command itself, it looks like you want me to update grub? I have not updated to Grub 2 btw... if i need to, i can simply do that thru the Update manager

And i did what you said above... and i get...

> ahl395@ahl395-PC:~$ sudo bash utils_alsa-info.sh
bash: utils_alsa-info.sh: No such file or directory
ahl395@ahl395-PC:~$ 


---

### Post by GameOverDood on 2010-03-06
> **lidex said:**
> There is a chance that you are not booting into the correct kernel if you just upgraded to karmic. To fix that, run these commands from a terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```Reboot

Oh hey that worked! Thanks. :)

Now let's just hope the OP managed to fix *his* issue...

---

### Post by lidex on 2010-03-06
> **ahl395 said:**
> Ok, well to your first post, i tried it. and it goes through and then asks me Y/n?
No matter which one i say it then says Abort after and stops. :/

By reading the command itself, it looks like you want me to update grub? I have not updated to Grub 2 btw... if i need to, i can simply do that thru the Update manager

And i did what you said above... and i get...

If you're not using grub2, post the output of this command:
```
uname -a
```
I wouldn't try updating that just yet. That code simply updates the grub entries from various configuration files. As for the script, your terminal defaults to your user directory, so if the file is not there it won't run. Verify the location of the script - it should be in:
/home/<your username>/utils_alsa-info.sh

---

### Post by ahl395 on 2010-03-06
Ok here is the output

> ahl395@ahl395-PC:~$ uname -a
Linux ahl395-PC 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
And i did put it in there... but ill tryagain

---

### Post by lidex on 2010-03-06
One other thing that could be helpful is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by ahl395 on 2010-03-06
Ok, sorry i was doing it wrong :S

lol, here is my output ^^

[http://pastebin.com/Q854umLF](http://pastebin.com/Q854umLF)


And here is the output to the last one you posted :)

> ahl395@ahl395-PC:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1259 F.... slmodemd
/dev/snd/pcmC0D6c:   Slmodemd   1259 F...m slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1259 F...m slmodemd
ahl395@ahl395-PC:~$ 


---

### Post by lidex on 2010-03-06
> **ahl395 said:**
> Ok, sorry i was doing it wrong :S

lol, here is my output ^^

[http://pastebin.com/Q854umLF](http://pastebin.com/Q854umLF)


And here is the output to the last one you posted :)

If you do not have a modem - or don't use it - run this command :
```
sudo apt-get remove sl-modem-daemon
```

And reboot!

---

### Post by ahl395 on 2010-03-06
Holy Crap! it worked!!!!!

Thank you so much! :):)

So, it was my modem causing the problem the whole time? :O

---

### Post by lidex on 2010-03-06
> **ahl395 said:**
> Holy Crap! it worked!!!!!

Thank you so much! :):)

So, it was my modem causing the problem the whole time? :O

You're welcome. Pretty much the modem driver was "stealing" the audio before the soundcard could get it. I noticed you have an HP Dv notebook, here is a site you'll want to bookmark:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")

Don't forget to mark the thread solved. (Thread tools, near the top)

---

### Post by ahl395 on 2010-03-06
> **lidex said:**
> You're welcome. Pretty much the modem driver was "stealing" the audio before the soundcard could get it. I noticed you have an HP Dv notebook, here is a site you'll want to bookmark:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing)

Don't forget to mark the thread solved. (Thread tools, near the top)

Ahh, okay :)

yep, i do. awesome! ill take a look, thanks again

---

### Post by redjess on 2010-05-28
> **RedSingularity said:**
> So nothing is playing sound?  In a terminal type 

alsamixer

and make sure all the levels are up.

I love you guys, you always fix my problems!

---


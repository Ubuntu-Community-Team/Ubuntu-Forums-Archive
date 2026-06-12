---
title: "Ubuntu and nVidia Graphics installation"
date: 2013-10-06
forum: Multimedia Software
---

### Post by fidbeck on 2013-10-06
I don't know if this is the most appropriate section to post this, since my problem can fall in 3 categories here in the forum, but i'm posting here anyway. If you think this should be in ano other place please move it.

Noiw to the problem...

I have a nVidia 9M series on my laptop ([NVIDIA GeForce 9600M GT]("http://www.notebookcheck.net/NVIDIA-GeForce-9600M-GT.9449.0.html")) and I want to install the proprietary graphic drivers. What's really the best way to do it?

I tried manually downloading the .run file from nVidia and tried to install it.
Opened the terminal and wrote sudo service lightdm stop and went to the shell screen, I logged in with my credentials and wrote sudo ./NameOfThefile.run and it did a integrity check, and asked my a few question which I said yes. One of them showed me a messageor w warning which I haven't read. It started to install and in the end I got the message saying that the graphic drivers were installed successfuly. Back in the shell I just wrote sudo reboot. the thing is that now I can't log back in Ubuntu because It does a kind of a services check and everything except one thing seems to be ok.
this is the message that it's been showed after a reboot
*Starting crash report submission deamon
saned disabled: edit /etc/default/saned
* Starting load fallback graphics devices      [fail]

first of all is there a way to revert this, if there is one, other than formatting :/

and what's the best way to install it?
- Going to the "Software and Updates" and choose the version
- This way
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
and it also says that we should remove xorg-edgers ppa this way
sudo add-apt-repository --remove ppa:xorg-edgers/ppa 
sudo apt-get update
sudo reboot

- or another way
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade

What's the best way?

---

### Post by Yellow Pasque on 2013-10-06
It depends on what version of Ubuntu you are running. Ubuntu 12.04.3 and 13.10 have nvidia-319 in the repos, so it's as simple as:
```
sudo apt-get install nvidia-319
```

If you're running 12.10. or 13.04, then use the x-swat PPA and install nvidia-319.

> I tried manually downloading the .run file from nVidia and tried to install it.
It's not a good idea to do it the "Windows way" as you've discovered...

---

### Post by Yellow Pasque on 2013-10-06
> first of all is there a way to revert this, if there is one, other than formatting :/

Well, if you can get to a terminal, then you run the nvidia installer again with --uninstall option.

---

### Post by fidbeck on 2013-10-06
Thanks [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") for the answer.
This is the screen I was talking about...
[http://i.imgur.com/42CbCSP.jpg](http://i.imgur.com/42CbCSP.jpg)
Once I get that screen, end of the line.

@[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")
I'm currently running Ubuntu 12.04.3 64bits and my kernel version is 3.80-31
 So can I just sudo ./NVIDIA-Linux-x86_64-319.60.run --uninstall and all starts working alright?
Since i'm running 12.04.3 what's really the best way to install it? ppa:ubuntu-x-swat or ppaorg-edgers and should I sudo apt-get install nvidia-current nvidia-settings or just update and upgrade? :S
and "It's not a good idea to do it the "Windows way" as you've discovered..." Yeah I found it the hard way :S

---


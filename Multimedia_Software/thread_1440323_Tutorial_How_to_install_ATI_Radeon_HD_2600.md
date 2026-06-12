---
title: "Tutorial: How to install ATI Radeon HD 2600"
date: 2010-03-27
forum: Multimedia Software
---

### Post by paulrogers on 2010-03-27
Ive had this problem twice now and eventually figured it out myself, but i keep forgetting, so this guide is for any of you out there that need help setting it up as well as a reference for me for everytime my system messes up.

First of all, open a terminal window (Applications --> Accessories --> Terminal)

Type in: lspci
You will see a big output, mine was near the bottom, find:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

```This means I have an ATI Radeon 2600, which im writing this guide for, if you have anything different, you are welcome to follow these instructions but I do not guarantee them working nor do I take any responsibility.

Go to: [http://www.amd.com/uk/Pages/AMDHomePage.aspx](http://www.amd.com/uk/Pages/AMDHomePage.aspx)

On the right, under Download Drivers:

Component Category = Graphics
Operating System: Linux x86 (if you have a 64bit system select the 64bit one)
Product Line: Radeon
Product Model: ATI Radeon 2xxx series

Click View Results

There was only 1 result for me, click Download, save it to your downloads folder.

When fully downloaded, go back to the terminal window and type in:

cd /home/paul/Downloads (change paul to your username)

then type:

sudo sh ati-driver-installer-10-3-x86.x86_64.run (if the filename is different, then change the name).

You will be asked for your password, enter it, it will take a few seconds then launch an installer.

Select the first option, then click next, then use all the reccomended options. When finished, restart your computer.

To get sound working right click on the sound icon on the top right, click sound preferences.

Go to Output and select the RV630 or whichever your one is.

If the sound still doesnt work, go into a terminal window again and type:
killall pulseaudio

Then type:
sudo alsa force-reload

Enter your password, press enter. Sound should work

This is just what worked for me after hours and hours of research, so I thought I would put it all in one place to help you people out. I tried to keep it as SIMPLE as possible. I take no responsibility for any loss of data, broken keyboards, cracked screens, melted mousemats etc etc, use at your own risk.

Anyone else feel  free to add commments or suggestions other users may use to make this even easier

Edit: Dont forget to enable desktop effects, its well worth it:
Right click on the Desktop
Click Change Desktop Background
Click Visual Effects tab
Select Extra, it can take a while and the screen goes weird while it makes changes.

---

### Post by coolcaseley67 on 2010-03-27
make sure you pin This post !!

---

### Post by fooey on 2010-03-31
why is this so straight forward? i have an ATI Radeon HD 2400 XT (on a work PC), and i've always had problems with drivers & ubuntu. although i swear i've tried this method before, i'm definitely going to try this again. maybe i can finally upgrade from 8.04 ;)

will update if it does make a difference..

---

### Post by ne0genius on 2010-05-02
Can anyone confirm extra desktop effects working on 10.04 with same install method. I keep getting  "Desktop effects could not be enabled"

using ati-driver-installer-10-4-x86.x86_64.run on 10.04-amd64

maybe an aticonfig setting? thanks

edit:
looks like there were errors in the fglrx-install.log
[http://pastebin.com/xiE7DZK7]("http://pastebin.com/xiE7DZK7")

---


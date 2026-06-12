---
title: "Problem with ati legacy driver 13.1 on ubuntu 12.04"
date: 2014-04-17
forum: Multimedia Software
---

### Post by jonathan-sancheez on 2014-04-17
Hi guys,
I'm writting from Chile.
I am a new user on Linux OS.

By the way, first i have to tell you that when i was installing Ubuntu 12.04 LTS on my PC, "Additional Drivers" shows my graphic card; Ati Radeon HD 2400 Pro.
But, when the installation finished, "Addiotional Drivers" never show it again.

I was reading some guides about How to install Legacy 13.1 on Ubuntu 12.04. However, my results were always bad.

Y put "X- version" on terminal and the result was: Xorg 1.14.1 (WoW)

I know that this driver doesn't work with Xorg over 1.12, so i think if i continue trying to install it i will never have good results.

On the other hand, in the ATI/AMD website, the requirements of this driver is kernel up to 3.5 and I think that my kernel is 3.6 (I guess, now i don't have my notes here. In the night i will edit this post)

So, what can I do?

I want to install the privative driver because with the Radeon driver i just have 59.5 FPS with "glxgears" command. I for me that is not enough.

If I apply the PPA of Tomasz Makewericz had designed an repository that downgrade my Xorg file to 1.12.* my graphic card will work?

Best Regards,

Jonathan Sánchez.

PS: I am so sorry if my English is not good. I am just trying to write in this languaje and for me is a little bit hard to do it.

---

### Post by jonathan-sancheez on 2014-04-17
** explanation of the first line **

I installed my new OS (Linux) with an LiveCD image on a USB stick.

After the installation finished, i reboot my computer, unplugged usb key and when I try to activate the privative driver, nothing appears there.

---

### Post by Bashing-om on 2014-04-17
jonathan-sancheez; Hi Welcome to the forum.

Are you aka "NosecuentA" from IRC #ubuntu ?

Fore ground:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


Current ground:
> 
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
Unfortunately, this links seems to be popping up in every thread where folks want to get AMD restricted drivers working with their HD 2x/3x/4x-series chipsets.

Problem is that folks don't read through the thread to notice that it requires downgrading your X-server to an older version.

This is trading short-term gains resulting from AMD driver installation to long-term risks of system corruption due to messing around with the X-server.

This option has actually been around for some time -- and I've been advising AGAINST it all that time -- it's just that this thread now exposes this approach to a wider audience.(Mark Phelps)

This is very likely to cause serious complications down the road as other updates come through.
You are trading a short-term improvements for serious long-term risks of system damage.

Need we say more ? .. stay with the open source drivers, OR upgrade your graphics card .

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by jonathan-sancheez on 2014-04-17
Yes. I am 'NosecuentA' in IRC.
We were talking this afternoon.

The only problem that i have now is that my Xorg version is 1.14 and I need to downgrade it in order to make work the propietary driver.

Will be dangerous that action? why?

Regards.

And thank you so much for your help!

---

### Post by Bashing-om on 2014-04-17
jonathan-sancheez; Well,

While one may "downgrade" to X-server v1.12, I feel it is better to backup all the personal data, and do a clean install of release 12.04.1.
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
Scroll down to the bottom of the page to find the link for the 12.04.1 image that you desire.
The .iso will no longer fit on a CD, one must burn to a DVD or USB.

Be aware the release 12.04.1 is still a Long Term Support release and continues to have full support 'till 2017.

Then one can install the proprietary FGLRX driver - suggest from the "Additional Drivers" utility - with no worries of system breakage.
Clean and solid from the start.

[INDENT]That is what I would do
[INDENT][INDENT][INDENT]would not advise you different
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jonathan-sancheez on 2014-04-18
Bashing-om,

Now im downloading it from the computer of my work.

In the night I will do the fresh installation of this iso.

After install the 12.04.1 i will be able to upgrade the actualizations that the system offers me?

Regards!

---

### Post by Bashing-om on 2014-04-18
jonathan-sancheez; Hello.

In the affirmative, yes once 12.04.1 is installed -> System Settings -> Additional Drivers. Install the recommended proprietary graphics driver.
To see how many frames per second your video card is putting out, run the following command:
```

glxgears -info

```
(also starts the glxgears graphic)

See what then you think.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by jonathan-sancheez on 2014-04-19
Hi,

I have a trouble.

I finished my installation of Ubuntu 12.04.1 as you suggested.

But i can't see the Propietary driver...

Should I add the repository in the sources?

[IMG]http://s2.subirimagenes.com/imagen/previo/thump_8881303captura-de-pantalla.png[/IMG]

Regards,

---

### Post by Bashing-om on 2014-04-19
jonathan-sancheez; Hi !

Are you still having problems ?

From what I can make out of the screen shot, that is not "Additional Drivers" - Ubuntu one ?,

Once booted up to the desktop, in the launcher - left side of the screen - is "System Settings" Click on "System Setting" and in the resulting pop up is "Additional drivers". Click on "Additional Drivers". Nothing ?
OK, let's see that the required repositories are enabled in "Software Sources", Main, universe and multiverse (defaults) are enabled as well as " third Party" software.
Reload the data bases:
```

sudo apt-get update
sudo apt-get upgrade

```

Now what do you see in "Additional Drivers" ?

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by jonathan-sancheez on 2014-04-19
Bashing-on,hi!

Today i will give it a try.

thank you in advance!!

---

### Post by Bashing-om on 2014-04-19
jonathan-sancheez; Hello once more,

It is my desire that you have a good experience with ubuntu.
If there is a problem with communications due to my usage of the English Language, please advise and I will try to simplify and explain better.

In the event there continues to be a problem with the hardware and installing a driver; Please post back the output of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

``` 
To see your graphics card and info: and to allow us to further assist in this small matter.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there are solutions there are no problems[/INDENT][/INDENT]

---


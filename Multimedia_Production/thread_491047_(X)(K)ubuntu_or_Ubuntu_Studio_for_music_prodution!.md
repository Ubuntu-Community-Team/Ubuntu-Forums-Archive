---
title: "(X)(K)ubuntu or Ubuntu Studio for music prodution?!"
date: 2007-07-03
forum: Multimedia Production
---

### Post by c_martini on 2007-07-03
I am  Kubuntu user and have recently seen that This Ubuntu Studio Distribution has been launched. 

Other than including music and multimedia production packages, what does this distro offer that the other flavours of Ubuntu don't?

I am what you would call a casual musician nowadays. In the past I have either been in studios with Pro Tools, racks of ADAT machines or hard disc based recording on Windows boxes. I have recently returned to home based music production after an absence of many years. My band is about 3,000 miles away from me so we collaborate over the net and through sending discs back and forth with demo tracks to dump into whatever DAW platform we happen to be using at the time.

Since dropping Windows in favour of Linux (Kubuntu) as my main O/S for most applications last year, I have really grown to appreciate the power of this platform and its potential. Now that I am returning to music again, I am evaluating its use as a home music recording setup. I still retain a Windows installation for my much loved pc games and the very few little apps that I cannot run in Linux. So I have the option of running my music production setup on either platform...

I have already built a more powerful machine with a good Linux supported sound card (M-Audio), and have purchased a decent usb condensor mic. I have looked into a few packages, such as Ardour with which to dump my bands tracks into and add my vocal lines...

So really what I would like to know is: 

Is it worth me installing the Studio specific Ubuntu distro or just installing relevant recording and audio packages in my Kubuntu setup? Does this Ubuntu Studio use some kind of low latency kernel specialised for audio/video production? Does it use some type of custom written drivers or software and make setting up a music production system easier?

I could not find any release notes describing the features specific to the Studio flavour of Ubuntu on the [http://ubuntustudio.org/]("http://ubuntustudio.org/") site or anywhere in the forums...

:?

---

### Post by TRinQtown on 2007-07-03
You can install the low latency kernel with Synaptic. And you can add the Ubuntu Studio repository without installing Ubuntu Studio.

---

### Post by morgan_greywolf on 2007-07-03
Ubuntu Studio is nice and integrated.  You get the Ubuntu Studio GNOME theme, which is a high-contrast theme with dark, neutral colors that is ideal for music production work (it helps by highlighting your work).  The low-latency kernel comes installed by default and you can get the realtime kernel, which gives you no X runs.

---

### Post by c_martini on 2007-07-03
> **TRinQtown said:**
> You can install the low latency kernel with Synaptic. And you can add the Ubuntu Studio repository without installing Ubuntu Studio.

Cool. And I imagine this repository has distribution specific versions of the apps (Ardour, JACK etc)?

> **morgan_greywolf said:**
> Ubuntu Studio is nice and integrated.  You get the Ubuntu Studio GNOME theme, which is a high-contrast theme with dark, neutral colors that is ideal for music production work (it helps by highlighting your work).  The low-latency kernel comes installed by default and you can get the realtime kernel, which gives you no X runs.

Well it surely looks nice from the screenshots. I wasn't sure I wanted to complicate my Kubuntu setup though by adding Gnome and its Ubuntu Studio theme as I already have KDE just the way i like it now. Although I imagine all the apps would most likely run under KDE just as well without Installing Gnome.

I don't mean to sound like a newb buts its been a looong time since I have used a pc to record music and i'm not sure what you mean by an 'x run'. I assume these are some type of kernel error?

---

### Post by Sweet Mercury on 2007-07-05
> **TRinQtown said:**
> You can install the low latency kernel with Synaptic. And you can add the Ubuntu Studio repository without installing Ubuntu Studio.

Just curious, where in the repository can I find that?

I added the US repositories to sources.list, and was able to install the US desktop (themes, sounds, etc) through Synaptic.  The US metapackage didn't include the kernel, though.

Also, side question, can I run the LL kernel using XFCE?

---

### Post by paulg on 2007-07-06
> **Sweet Mercury said:**
> Also, side question, can I run the LL kernel using XFCE?

Yes, just like any other 'bu' you are free to install/configure/use any window manager you wish. Whether it's Gnome, KDE, XFCE, Fluxbox etc.

Studio consists of the Feisty packages, relying on the same core Feisty repositories as Ubuntu, Kubuntu and Xubuntu and an additional 'Studio' repository that gives you the latest and greatest of the OSS media production world.

---

### Post by Sweet Mercury on 2007-07-06
> **paulg said:**
> Yes, just like any other 'bu' you are free to install/configure/use any window manager you wish. Whether it's Gnome, KDE, XFCE, Fluxbox etc.

Studio consists of the Feisty packages, relying on the same core Feisty repositories as Ubuntu, Kubuntu and Xubuntu and an additional 'Studio' repository that gives you the latest and greatest of the OSS media production world.

Alright, thanks.

I pretty much installed, through the studio repositories, the whole US package. I like.

---

### Post by guitard00d on 2007-07-09
> **c_martini said:**
> I don't mean to sound like a newb buts its been a looong time since I have used a pc to record music and i'm not sure what you mean by an 'x run'. I assume these are some type of kernel error?

It's an error that commonly occurs in the Jack audio server. It is kernel related, but it is also device related too (if you use a USB audio interface, x-run errors are an everyday occurrence). It's a bottleneck issue, you can look at it much like a buffer under-run or over-run on a CD burner. Only, rather than the problem affecting the CD burner, it's affecting the sound going in and coming out of your computer.

---

### Post by guitard00d on 2007-07-11
> **c_martini said:**
> Other than including music and multimedia production packages, what does this distro offer that the other flavours of Ubuntu don't?

Sorry to say this (I've got my flame protective gear on as I type this)...But the main thing Ubuntu Studio offers that the others don't - is a nice looking Gnome theme. The next things on the list that it offers are instability, unreliability and incompleteness.

Sorry, I've been playing with it for a week now and you're just better off installing plain Ubuntu and then installing the programs you want as needed (as well as the low latency kernel). Ubuntu Studio is a nice concept, and it has a pretty face on it, but it's just not put together as well as the other *ubuntu distributions.

It couldn't even detect the generic ATI Rage 128 video card in the system I was testing it on. It set xorg to "vesa" for the video driver when it should have been "r128" like plain Ubuntu selects. Power management didn't work in Ubuntu Studio, but it works just fine when running plain Ubuntu on the system. It took forever for the network card to configure, so every service that used a TCP/IP port would bind to 127.0.0.1 until I manually restarted those services after Gnome was up and running. Again, this problem doesn't exist in plain Ubuntu on the same system. A number of programs included in Ubuntu Studio wouldn't even start up, 3/4 of the OpenOffice.org launchers are missing, and there are numerous other oddities in it that would take me far too long to document.

So, I have to say that Ubuntu Studio isn't ready for prime-time. I think they were a little to eager to try and make a name for themselves in the Linux music scene and rushed a half finished project out the door. Save yourself a headache, just use plain Ubuntu and install the programs/kernel you want and they will work just fine.

---


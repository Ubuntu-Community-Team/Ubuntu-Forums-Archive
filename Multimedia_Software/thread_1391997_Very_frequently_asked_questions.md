---
title: "Very frequently asked questions"
date: 2010-01-27
forum: Multimedia Software
---

### Post by J V on 2010-01-27
I've spent a lot of time in the help forums recently, and I've come up with a list of questions often asked.

**Index**
Flash, MP3, Java
How to install programs
How to run windows programs
Viruses
Firewall
iPod, iTunes

**Flash, MP3, Java**
One of the first things you should install after you start up Ubuntu is  "[ubuntu-restricted-extras]("http://ubuntuforums.org/ubuntu-restricted-extras")" (Click to install)

This will install 32-bit adobe flash, and codecs.

Open source flash is already installed on ubuntu, but it is not as good as the one adobe make.

If you are on a 64-bit computer, you will need to install the 64-bit flash, which you can download, nice and neatly, from [adobes website]("http://labs.adobe.com/downloads/flashplayer10_64bit.html"). (Beyond the scope of this guide)

Codecs (programs that let you open video files) will also be installed, which will let you watch almost all videos. Some codecs will only be installed if you actually open a file that needs them, but this will only take a few seconds anyway.

Another often-used program is "[Java]("apt://sun-java-bin")" (Click to install)

**How to install programs**
If you come from windows, you will be used to downloading a setup program, and letting it install your application. In Linux, things are easier.

All you have to do is go to the software center in the applications menu, type in the name of the program, and double-click it.

The advantages are that it is much simpler, and that all updates will be gathered at once, so you don't have 10 different programs looking for updates at the same time.

Anything in the software center is good, everything outside could be bugged, or a hack to leave your system open to a malicious person, so always check before installing something you have to download.

**How to run windows programs**
Most people will tell you to run windows programs through "Wine", which, by the way is [not an emulator]("http://wiki.winehq.org/Debunking_Wine_Myths#head-7c9ecddfaff60d8891414b68d74277244e7109eb"), however, it can be hard to get going, and even if you like tinkering with stuff, there are easier ways.

"[Playonlinux]("apt://playonlinux")" (Click to install) is an excellent interface for wine, which has lots of options, and lots of enhancements, including separate settings for each program, separate wine versions for each program, and even windows-like "Next next next" installers that make running windows programs a LOT easier.

Firstly though, you should check weather a program works with the wine "[AppDB]("http://appdb.winehq.org/")"

**Viruses**
Linux has no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:

[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]
 On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

**Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall.

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

**iPod, iTunes...**
I can't claim to know much about Mac merchandise, in fact, I've never touched a mac keyboard in my life!

Nevertheless, iTunes, iPod, and iPhone are extremely popular machines that lots of people use.

iTunes 7 is the most compatible version (With Wine), but as always, it won't be as good as on windows, until apple decides to give a... coin... for its customers.

Also, "[Amarok]("apt://amarok")" (Click to install) and "[Banshee]("apt://banshee")" (Click to install) are somewhat compatible with iPod, but from what I've heard they are less than perfect.

People tend to install another open source OS known as [Rockbox]("http://www.rockbox.org/") on their iPods rather than trial and error their way through Amarok and Banshee.

Again, I'm by no means an expert on i<youNameIt>, but others are, consult them for information on the [iPod]("https://help.ubuntu.com/community/PortableDevices/iPod"), [iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone"), and [iTunes]("http://www.psychocats.net/ubuntu/itunes")

---


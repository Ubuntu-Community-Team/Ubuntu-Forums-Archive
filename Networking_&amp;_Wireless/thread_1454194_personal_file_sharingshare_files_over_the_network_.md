---
title: "personal file sharing/share files over the network doesn't work"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by jiggling_john on 2010-04-14
I'm using 10.04 beta...

If I go to system - preferences - personal file sharing, I cannot select "share files over the network." The panel is greyed out and the message "This feature cannot be enabled because the required packages are not installed on your computer" is shown

It ever so usefully doesn't tell me what those packages are though! - It'd be nice to have more useful error messages or the ability to click to install them...

Anyway, what do I have to do to get this going again?! I've installed everything to do with samba, webdav that I can find but still no cigar...

---

### Post by 98cwitr on 2010-04-14
how did you install samba?

---

### Post by jiggling_john on 2010-04-20
I used apt-get... I also tried through the software centre as well...

Surely this should just work from default though? What packages are required?

---

### Post by SuperMau on 2010-04-28
Yes, it is confusing, there is already a bug filled in about this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766)

Anyway, curious enough you need to install apache2.2-bin and lib-apche2-mod-dnssd and restart.


Cheers
SuperMau

---

### Post by user333 on 2010-05-01
I have this problem too

---

### Post by d00derino on 2010-05-01
Hey guys, I just posted a guide I found on using Samba. It's super easy (I speak from experience. I had Samba working before a fresh install to 10.04 and it was hell) and very new-user friendly. It's posted here: [http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

If you like it please give the original writer some props or comments. It's a very easy guide and got me running Samba in less than 10 minutes.

---

### Post by pmofidi on 2010-05-12
I have the same problem.
I have done the a/m steps but the problem still remains.
I have installed WinXP in VM . i am trying to share some folder with Win XP.
It was working for a few days but i dont know why i lost!
Please guide.

---

### Post by WolfRage on 2010-06-05
I figured it out, sorry but I believe my way is easier and I just want  to spread the word. Please see here: [http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

---

### Post by emaydubya on 2010-07-04
Been trying to get NFS working for about 5 hours now. No I don't want Samba.
I will now smash something and break some stuff to help me feel better.
Why there are no simple tools to get this done is a .... (insert your sentence here)

---

### Post by alpharaptor on 2011-01-23
There is a way to get network sharing working without having to install Apache.  Go to Preferences, Main Menu (or run alacarte).  Go down to Administration and under Show Item check "Shared Folders."  Apparently Ubuntu left this option disabled by default.  Now go to System, Administration and click Shared Folders.  You will get a message saying that software needs to be installed.  Click the padlock and enter the admin password.  It will download and install the necessary files including Samba.  It will need to be rebooted before the changes will take effect.  After rebooting go to System, Administration, Shared Folders and you'll be able to access all the settings for Workgroup name, Users as well as telling it what folders to share.  All this trouble because Ubuntu didn't enable a menu item.

---

### Post by abelmaio on 2011-05-27
I think the true solution for the "Personal File Sharing" being disabled is a little simpler.

All you have to do is, open the terminal and run:

```
sudo apt-get install apache2.2-bin libapache2-mod-dnssd
```

After that you may need to reboot the computer. 

Now if you go again to the "Personal File Sharing" menu, the option that was greyed now is enabled.

Don't really need to install any other kind of program to solve this.


I tryed on my Ubuntu 11.04 and worked fine. :D


Hope I could help.

---

Source: [http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/](http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/)

---

### Post by zeddock on 2011-06-06
> **abelmaio said:**
> I think the true solution for the "Personal File Sharing" being disabled is a little simpler.

All you have to do is, open the terminal and run:

```
sudo apt-get install apache2.2-bin libapache2-mod-dnssd
```

After that you may need to reboot the computer. 

Now if you go again to the "Personal File Sharing" menu, the option that was greyed now is enabled.

Don't really need to install any other kind of program to solve this.


I tryed on my Ubuntu 11.04 and worked fine. :D


Hope I could help.

---

Source: [http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/](http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/)


Worked on 11.04 but only to check the box....  still can't access anything from Ubuntu while on Windows7... It keeps asking for a username and password, but looks like windows wants the username to be DOMAIN/username.

How could I proceed?

zeddock

---

### Post by abelmaio on 2011-06-07
> **zeddock said:**
> Worked on 11.04 but only to check the box....  still can't access anything from Ubuntu while on Windows7... It keeps asking for a username and password, but looks like windows wants the username to be DOMAIN/username.

How could I proceed?

zeddock


Hello zeddock.

In fact, thats happen to me too. And I don't know what you must put to "login".

But I'll tell you what I do when I want to share files between my two computers on my home network, one with Linux and the other with Windows.


First I created a folder and named it "Shared"(Doesn't matter the name). Then, righ-clicked it and go to Properties.

Then, I went to the Shared tab and checked all the boxes. This depends on what you want.

I created the shared folder. 


Now, on my Windows (7) computer I went to Network and there was my Linux PC. Opened it and there was the Shared folder. 


This is how I usually proceed when I want to share files between two computers on my network.



If you use your computer on public networks, you must remember that anyone could access your Shared folder. You can desable the Sharing option or simply empty the folder (or leave the files if you don't care that other people access them).


This is how I do it. ;)


Don't know if I helped.



AM

---

### Post by zeddock on 2011-06-07
That is a good band-aid solution. I will use it.  But it irritates me when things don't work as advertised.  I suppose I have gotten used to this for Windows... not that it is bad, but that it usually works...  It is when things go wrong that thing go REALLY wrong and there are few options.

I have always felt that Linux, and Ubuntu for me, were trying to keep things simple, allow me to work and stay out of the way... but giving me the ability to "tweak" things if needed.

I consider this missing link a big deal...

I hope someone can figure out the problem and document the fix for us.

Until then, I will try to build a share folder, and see if it works.  Seems to me if your solution works without needing credentials, the other sharing should too.. it must just be configured incorrectly.

zeddock

---

### Post by abelmaio on 2011-06-08
Ubuntu try hard to make Linux the most user-friendly for all. 

And I agree with you. When things go wrong they really go wrong. 
But when you understand why and fix it's such a great pleasure. It's like a puzzle. :P 

I think the problem may be some kind of configuration.

If I find something about this I'll post here in this thread.


AM

---

### Post by Morbius1 on 2011-06-08
Boy there's a lot of confusion in this topic. Just in case someone actually does a search in this forum for "Personal File Sharing":

** [1] Personal File Sharing**

This utility comes from the package gnome-user-share. It's in the Menu  and can be invoked from the termial by the command:
```
gnome-file-share-properties
```It sets up a tiny apache file server and announces it presence to the rest of the network using avahi. As stated previously it requires you to install the following packages:
```
apache2.2-bin
libapache2-mod-dnssd
```It will only share one folder - /home/username/Public - although there are ways around this. 

You can set this Public share to require no passwords or prompt the client to supply a password. There are no credentials ( user name and password ) in the Samba sense because there are no users - it's only ON / OFF password protected. And it has nothing to do with accessing anyone else's shares on the network. It's only to provide a share on your box to others on the LAN.

Between two Linux boxes both of which have avahi installed and running it works fairly well. Interoperability between Linux and Windows or Macs is problematic in my use.

[COLOR=Blue]Personal File Sharing is not Samba - has nothing to do with Samba[/COLOR]

** [2] Nautilus-share** **( Samba Usershares )**

This is Samba. The nautilus-share package allows a user to share any folder he owns by right clicking on it from Nautilus. There's a corresponding mechanism in KDE as well. Here again this has nothing to do with accessing anyone else's shares on the network. It creates shares for others on the network to access.

Two different mechanisms - two different protocols.

---

### Post by abelmaio on 2011-06-08
> **Morbius1 said:**
> Boy there's a lot of confusion in this topic. Just in case someone actually does a search in this forum for "Personal File Sharing":

** [1] Personal File Sharing**

This utility comes from the package gnome-user-share. It's in the Menu  and can be invoked from the termial by the command:
```
gnome-file-share-properties
```It sets up a tiny apache file server and announces it presence to the rest of the network using avahi. As stated previously it requires you to install the following packages:
```
apache2.2-bin
libapache2-mod-dnssd
```It will only share one folder - /home/username/Public - although there are ways around this. 

You can set this Public share to require no passwords or prompt the client to supply a password. There are no credentials ( user name and password ) in the Samba sense because there are no users - it's only ON / OFF password protected. And it has nothing to do with accessing anyone else's shares on the network. It's only to provide a share on your box to others on the LAN.

Between two Linux boxes both of which have avahi installed and running it works fairly well. Interoperability between Linux and Windows or Macs is problematic in my use.

[COLOR=Blue]Personal File Sharing is not Samba - has nothing to do with Samba[/COLOR]




The problem is that this don't work as announced. I do that and no folder is shared on my network between different OS.

But if I make as I sayed, by right-clicking and go to the shared tab, then everything works. 

But the default *gnome-file-share-properties* does not work for me properly. :confused:

---

### Post by Morbius1 on 2011-06-08
OK, that means Samba works for you and gnome-user-share doesn't. The problem with this topic is that people are equating Samba with "Personal File Sharing" It's 2 different things. And the solution to fixing one is not relevant to the other. 

People doing a search for Personal File Sharing are looking for a fix for that not Samba. It's the same as asking for help about Samba and being told to use NFS.

---

### Post by abelmaio on 2011-06-08
> **Morbius1 said:**
> OK, that means Samba works for you and gnome-user-share doesn't. The problem with this topic is that people are equating Samba with "Personal File Sharing" It's 2 different things. And the solution to fixing one is not relevant to the other. 

People doing a search for Personal File Sharing are looking for a fix for that not Samba. It's the same as asking for help about Samba and being told to use NFS.


I know and I agree. I was also searching about personal folder sharing. And I saw a lot of people talking about installing SAMBA. 

The first question about this thread was about not being able to check the checkbox of the Share Option.
I told what I knew, installing the missing packages. And that fixed the checkbox problem. 

Then, after the checkbox was enabled, there was also a problem about the sharing option. 

So I only told people how I do to share files between diferent OS. I know it's a little offtopic. I'm sorry for that. But was only to inform how I solved the sharing problem. I didn't install SAMBA. I only use native functionalities of Ubuntu without installing anything.


The personal file sharing doesn't work for a lot of people and I haven't found a solution yet. :confused:



AM

---

### Post by Morbius1 on 2011-06-08
> **abelmaio said:**
> The personal file sharing doesn't work for a lot of people and I haven't found a solution yet. :confused:AM
Do you have bonjour installed on Windows? Bonjour is the Windows ( actually it was originally created by Apple ) equivalent of avahi. If you have just about any Apple product like iTunes it slips in bonjour without telling you. For all practical purposed PFS is strictly a Linux only file sharing system.

---

### Post by abelmaio on 2011-06-08
> **Morbius1 said:**
> Do you have bonjour installed on Windows? Bonjour is the Windows ( actually it was originally created by Apple ) equivalent of avahi. If you have just about any Apple product like iTunes it slips in bonjour without telling you. For all practical purposed PFS is strictly a Linux only file sharing system.

Yes I have Bonjour (iTunes). I didn't know that Bonjour was also needed. 
But even with Bonjour installed this don't work.

In truth, that's not very practical for people that just want to share files on the network. :(

But the SAMBA alternative worked for me. It seems simpler and other people don't need to have any special software installed.


Who may want help for the PFS is zeddock. 

But is good to know that kind of things. 
Thanks. :)


AM

---

### Post by capscrew on 2011-06-08
> **Morbius1 said:**
> Do you have bonjour installed on Windows? Bonjour is the Windows ( actually it was originally created by Apple ) equivalent of avahi.  If you have just about any Apple product like iTunes it slips in bonjour without telling you.

For the sake of completeness: Microsoft refers to this as Automatic Private IP Addressing (APIPA)  Bonjour is Apple's term for it.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://msdn.microsoft.com/en-us/library/aa505918.aspx") for Microsoft's take on the subject.
> 

For all practical purposed PFS is strictly a Linux only file sharing system.

The original Term for what Ubuntu calls Personal File Sharing is WebDAV (see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/WebDAV")).  The protocol makes the Web a readable and writable medium. It provides a framework for users to create, change and move documents on a server (typically a web server or "web share").   This is why Apache is installed.  The WebDAV official site is [**_[COLOR="DarkSlateGray"]http://www.webdav.org/[/COLOR]_**]("http://www.webdav.org/").

Just saying...:D

---

### Post by eigentlichgewesen on 2011-08-13
> **alpharaptor said:**
> There is a way to get network sharing  working without having to install Apache.  Go to Preferences, Main Menu  (or run alacarte).  Go down to Administration and under Show Item check  "Shared Folders."  Apparently Ubuntu left this option disabled by  default.  Now go to System, Administration and click Shared Folders.   You will get a message saying that software needs to be installed.   Click the padlock and enter the admin password.  It will download and  install the necessary files including Samba.  It will need to be  rebooted before the changes will take effect.  After rebooting go to  System, Administration, Shared Folders and you'll be able to access all  the settings for Workgroup name, Users as well as telling it what  folders to share.  All this trouble because Ubuntu didn't enable a menu  item.



thanks that fixed my problem straight away! so easy.

---

### Post by Bucic on 2011-12-14
> **Bucic said:**
> Do you get a message in personal file sharing preferences about some missing packages? If so:
- install synaptic through ubuntu software center
- install apache2 through synaptic
from another topic...

---

### Post by gshreya3 on 2012-04-10
I am facing the same problem to share files over the network. Please help.

Thanks in advance.

---


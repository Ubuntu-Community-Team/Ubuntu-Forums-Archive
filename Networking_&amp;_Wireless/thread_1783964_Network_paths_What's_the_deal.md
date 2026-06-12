---
title: "Network paths? What's the deal?"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by windyweather on 2011-06-16
Paths displayed in Nautilus appear to be just that. Nautilus private syntax. Esp with respect to anything "special".

Am I wrong?

Apparently when you hand a path like this to a program to open, you get a folder in your home directory:
smb://cyberstorm/c_drive/

At least that is what my program does with it. A folder called smb: in my home directory. Probably because the default folder for the program is the home directory [~].

Is there a universal network folder syntax for the network and other "special" file systems?

I see things like: network:/// and computer:/// showing up in "properties" dialogs for some things. But these are useless to a program apparently.

At least a program written in Qt.

Is this a Qt problem, or a problem with Ubuntu not yet making the network a first class citizen in the world of paths?

Who do I complain to?

Time for the network to be a first class citizen, right?

- ww

---

### Post by Morbius1 on 2011-06-16
I have no idea if this answers your question but if you type in nautilus:
> smb://cyberstorm/c_drive/A mount point is created here:
> /home/you-user-name/.gvfs/c_drive on cyberstorm

---

### Post by windyweather on 2011-06-16
Ok. Sounds like there is a deep hack. But from a user point of view, running a file open dialog or folder open dialog in a program, this is not what we want, right?

We want to just browse in the file / folder dialog and navigate to the network file shares, right? Or copy/paste the Nautilus location path into the program, right? After all that's the way it works it other Eh Hem, systems, right?

And we want this to work for Samba [WFS - windows file sharing], NFS, and all the other network classes, right? Are they any others that folks use? Anybody still use NFS for anything? I assume so.

Anybody know how it works on the-Eh Hem - Mac? Is the network a first class citizen in the world of paths, or a special purpose hack?

- ww

---

### Post by Morbius1 on 2011-06-16
The "file open" will only point to things that are mounted it can't initiate a mount of a remote share.

So you need to mount the remote share first and then it will show up in "file open" in the user's home directory under the ".gvfs" folder.

---

### Post by redmk2 on 2011-06-17
> **windyweather said:**
> Paths displayed in Nautilus appear to be just that. Nautilus private syntax. Esp with respect to anything "special".

Am I wrong?

Yes you are.  :-(> 


Apparently when you hand a path like this to a program to open, you get a folder in your home directory:
smb://cyberstorm/c_drive/

At least that is what my program does with it. A folder called smb: in my home directory. Probably because the default folder for the program is the home directory [~].

Is there a universal network folder syntax for the network and other "special" file systems?

Yes there is.  What you are describing are Universal Resource Identifiers (URI).  You can read all about them [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/Uniform_Resource_Identifier").  The section on the relationship to URL's and URN's is enlightening. > 

I see things like: network:/// and computer:/// showing up in "properties" dialogs for some things. But these are useless to a program apparently.

To some programs that is true.  But then again .pdf, .xls or .odt files are useless to some programs too.> 

At least a program written in Qt.

Is this a Qt problem, or a problem with Ubuntu not yet making the network a first class citizen in the world of paths?
I would not call it a problem.  I think it is a lack of understanding on your part.> 

Who do I complain to?
Nobody> 

Time for the network to be a first class citizen, right?
???> 

...**Ok, so there's a hack?**

Ok. Sounds like there is a deep hack. But from a user point of view, running a file open dialog or folder open dialog in a program, this is not what we want, right?

It is if you are using URI's (or URL/URN) in a file browser,  web browser or some such.> 

We want to just browse in the file / folder dialog and navigate to the network file shares, right? Or copy/paste the Nautilus location path into the program, right? After all that's the way it works it other Eh Hem, systems, right?

Windows Explorer uses URI/URL/URN's also.  i believe Apple Finder uses them too.  URI's are well known entity.  Once again these are not file paths. > 

And we want this to work for Samba [WFS - windows file sharing], NFS, and all the other network classes, right? Are they any others that folks use? Anybody still use NFS for anything? I assume so.

Anybody know how it works on the-Eh Hem - Mac? Is the network a first class citizen in the world of paths, or a special purpose hack?

- ww


Apple uses the same conventions as all the others.  the others.  WFS and Samba use URI's and (Universal Naming Convention (UNC) to locate SMB resources.  NFS is an implementation of RPC's to mount a remote Unix style file system to a local Unix file system.  It does not use URI or UNC at all.  Sun developed NFS without regard to the Internet.  As a LAN technology for mounting unix file systems to other unix file systems, Sun didn't see any need for URI/URL's.

---

### Post by windyweather on 2011-06-17
Thanks for your long answer. I'll read the link and the whole thing when I get some time. But you may have missed the point. See it doesn't matter what kind of uthingy it is or isn't. Or where you get it. My point is simple, as follows:

Whatever uthingy that Nautilus uses should be the same uthingy [or several types] that the file/folder browser brought up by things like QFileOpenDialog or QFileSaveDialog and their counterparts in other libraries like Gnome or KDE etc. And the set of Uthingies understood by the File Dialogs should include all types of networks as well as the files on the local system.

And don't give me the Mount argument. Just automount it when it's accessed. And if the network sw is installed for some network then a hub for that network should appear in the file browser.

Problems currently are:
1 - no network hub in the file browser for WFS [samba] on ubuntu. Not sure about NFS since I have never installed that one since I have no other servers on my network.
2 - file browser from a program does not understand uthingys that Nautilus uses. They should both understand the same syntax. What's the point of nautilus providing a uthingy in the location bar if the only consumer of the uthingy is nautilus itself?

Maybe #2 is a problem with Qt library, I have not used other language libraries [well I did use KDE, but that was a long time ago.].

Does that make my concerns more clear? And yes there is someone to complain to: The entire community. I may be confused about uthingy's, but that doesn't effect my concerns, since the details of uthingy's are outside the scope of the complaint. Which uthingy's are used or not used by whatever software is an implementation detail. Pick a set that every component supports so programs, File Dialogs and Nautilus [and your flavor of the month file browser program] all understand.

Thanks for understanding,
ww

---

### Post by redmk2 on 2011-06-18
> **windyweather said:**
> Thanks for your long answer. I'll read the link and the whole thing when I get some time. But you may have missed the point. See it doesn't matter what kind of uthingy it is or isn't. Or where you get it. My point is simple, as follows:

Whatever uthingy that Nautilus uses should be the same uthingy [or several types] that the file/folder browser brought up by things like QFileOpenDialog or QFileSaveDialog and their counterparts in other libraries like Gnome or KDE etc. And the set of Uthingies understood by the File Dialogs should include all types of networks as well as the files on the local system.
The URI/URL protocol is a standard for all.  All languages understand the construct and deal with the same way.  It doesn't matter whether it is perl, python, C++, Java, GTK or Qt.  The application developer my choose to implement all or parts of the capability.  As an example Firefox can handle HTTP, HTTPS, FTP and SMB.  But not COMPUTER or NETWORK.  The Protocol is there,  The libs are there.  The developers use the part that they need.   > 

And don't give me the Mount argument. Just automount it when it's accessed. And if the network sw is installed for some network then a hub for that network should appear in the file browser.
Okay.  What do you mean by *network sw and hub?*> 


Problems currently are:
1 - no network hub in the file browser for WFS [samba] on ubuntu. Not sure about NFS since I have never installed that one since I have no other servers on my network.
2 - file browser from a program does not understand uthingys that Nautilus uses. They should both understand the same syntax. What's the point of nautilus providing a uthingy in the location bar if the only consumer of the uthingy is nautilus itself?

Maybe #2 is a problem with Qt library, I have not used other language libraries [well I did use KDE, but that was a long time ago.].

Qt does have a class that handles URI/URL information.  Maybe you are not familiar with the [**_[COLOR="SeaGreen"]QUrl Class[/COLOR]_**]("http://doc.qt.nokia.com/latest/qurl.html")? > 

Does that make my concerns more clear? And yes there is someone to complain to: The entire community. I may be confused about uthingy's, but that doesn't effect my concerns, since the details of uthingy's are outside the scope of the complaint. Which uthingy's are used or not used by whatever software is an implementation detail. Pick a set that every component supports so programs, File Dialogs and Nautilus [and your flavor of the month file browser program] all understand.

Your concerns seem clear.  Your complaints relate to lack of a standard.  I say that the standard is there and Qt supports it.  URI/URL's are described in [RFC 1738]("http://tools.ietf.org/html/rfc1738") in 1994.> 

Thanks for understanding,
ww

I'm not sure I do understand your point.  If you have a gripe with the implementation, then talk to the implementor.  In this case it would be Gnome (Nautilus).

Ubuntu as a distro just packages the Linux kernel and Gnome along with the other parts to create the OS.  The development is upstream of Ubuntu and Debian.  Complaining here in a user forum is not productive to changes in Gnome's Nautilus.

---

### Post by windyweather on 2011-06-19
> I say that the standard is there and Qt supports it. URI/URL's are described in RFC 1738 in 1994.
I'm not clear how this relates to File Sharing. Again, I'm not concerned with File/network path syntax, but with apparent implementation. I can't navigate in Qt's Open File Dialog with Samba installed, so something has not been implemented somewhere.

> What do you mean by network sw and hub?
Network Software - the software that implements file sharing over the network. WFS[Samba] and NFS are examples. Hub - An item that appears in the File Browser that lets you navigate to network shared files on other computers, whether they are yet mounted or not.

> I'm not sure I do understand your point.
I can't navigate in the Open File Browser to the network shared files. I should be able to. If I can't so navigate then I can't tell a program where to find network shared files. After all, I don't want to hard code the network share paths into the code or type them in, I need to be able to navigate to them. And installing the network file sharing client software [Samba, NFS, etc.] should be enough to cause that to happen.

Is that clear?
Thanks for your thoughtful response,
ww

---

### Post by redmk2 on 2011-06-19
> **windyweather said:**
> ... I'm not concerned with File/network path syntax, but with apparent implementation. I can't navigate in Qt's Open File Dialog with Samba installed, so something has not been implemented somewhere.
Ahhhhh, so your not interested in creating an app for Qt, rather you are attempting to access a Samba (SMB) file share on Ubuntu from a hand held device.  What exactly are you doing?  A step by step process would be nice.> 

Network Software - the software that implements file sharing over the network. WFS[Samba] and NFS are examples. Hub - An item that appears in the File Browser that lets you navigate to network shared files on other computers, whether they are yet mounted or not.

I understand now.> 

I can't navigate in the Open File Browser to the network shared files. I should be able to. If I can't so navigate then I can't tell a program where to find network shared files. After all, I don't want to hard code the network share paths into the code or type them in, I need to be able to navigate to them. And installing the network file sharing client software [Samba, NFS, etc.] should be enough to cause that to happen.

Is that clear?
Thanks for your thoughtful response,
ww

Now that I understand what you are attempting to do, it sounds like a limitation of Qt's file browser implementation.  What did you mean with  your reference to KDE earlier?  AFIK Samba performs the same on all Linux based platforms.  The file browser functionality is the determined by its authors (i.e. Gnome (Nautilus), KDE. Qt(?), etc.).

**Edit:** Could this [**_[COLOR="DarkSlateGray"]plug-in[/COLOR]_**]("http://www.freeware4android.net/samsung-gt-s5570-galaxy-mini-device-1868/browser-addons-search-tag/ghost-commander-samba-plugin-download-31062.html") be what you're looking for?

---

### Post by windyweather on 2011-06-21
Nope. Don't need the Android plugin.

At the moment, I'm developing Qt apps. But I'm not restricting my comments to Qt apps. Mobile is part of the larger picture, of course.

So you are saying that this is a bug in the Qt implementation of the file / folder browser dialog? Can you show me an app written in another environment that works correctly with at least Samba on Ubuntu 10.04/11.04? I'd like to see how it works and compare it with other situations on other platforms.

Once I have an example of correct behavior I can reference that in the bug to Qt. - If anybody is still home over there. Were they all sent home when MS bought into Nokia for Phone-7? Maybe Qt will revert to TrollTech or somewhere else, or become entirely open source.

Thanks,
ww

---

### Post by redmk2 on 2011-06-21
> **windyweather said:**
> Nope. Don't need the Android plugin.

At the moment, I'm developing Qt apps. But I'm not restricting my comments to Qt apps. Mobile is part of the larger picture, of course.

So you are saying that this is a bug in the Qt implementation of the file / folder browser dialog? 
As far as I can tell there is no bug in Qt.  Rather a lack of understanding on your part.  File paths are a local thing.  To locate files remotely you need to use a URL (thingy).  URL/URI's are already  implemented in Qt.

The question may be where are the files  you are using relative to the Qt app and what protocol are you using to address them?  Samba and WFS use the protocol SMB and therefore need URL/URI functionality in the app.   > 

Can you show me an app written in another environment that works correctly with at least Samba on Ubuntu 10.04/11.04? I'd like to see how it works and compare it with other situations on other platforms.

The one I recommended does just that for any Samba implementation. The fact that Samba is hosted on a Ubuntu host is at most incidental.  The protocol SMB (CIFS, WFS, etc, etc,) is the driver here. 
The Google search would be: Qt + URL> 

Once I have an example of correct behavior I can reference that in the bug to Qt. - If anybody is still home over there. Were they all sent home when MS bought into Nokia for Phone-7? Maybe Qt will revert to TrollTech or somewhere else, or become entirely open source...


Hmmmmmmmmmmmmmmm

---


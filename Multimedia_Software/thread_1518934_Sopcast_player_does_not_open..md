---
title: "Sopcast player does not open."
date: 2010-06-27
forum: Multimedia Software
---

### Post by bhishan on 2010-06-27
I use Ubuntu Lucid Lynx. Sopcast player used to work properly, but from yesterday it does not open at all. It doesnt open when I click a link or even when I try to open from the menu. Anyone else having the same problem?

---

### Post by howefield on 2010-06-27
Did you upgrade VLC to 1.1 ?

Sopcast doesn't work with the new VLC.

Start sopcast via the terminal to get an idea of what the problem is.

---

### Post by bhishan on 2010-06-27
> **howefield said:**
> Did you upgrade VLC to 1.1 ?

Sopcast doesn't work with the new VLC.

Start sopcast via the terminal to get an idea of what the problem is.

How do i start sopcast via the terminal?

---

### Post by howefield on 2010-06-27
I'm on the laptop and sopcast is installed on the desktop but I think if you open a terminal and type 

```
sopcast-player
```

that should open sopcast or if not, give you an error pointing to why it can't.

---

### Post by bhishan on 2010-06-27
> **howefield said:**
> I'm on the laptop and sopcast is installed on the desktop but I think if you open a terminal and type 

```
sopcast-player
```

that should open sopcast or if not, give you an error pointing to why it can't.

Thanks, the problem was because of VLC 1.1 as you said. I removed it and installed the old one, Sopcast is working now.

---

### Post by howefield on 2010-06-27
Glad you're sorted, I had to do the same.

Might be worth subscribing to this thread, the developer is active and has posted, so may get an update as to when/if sopcast will be made to work with VLC 1.1...

[http://ubuntuforums.org/showthread.php?t=1032901&page=42](http://ubuntuforums.org/showthread.php?t=1032901&page=42)

---

### Post by bhishan on 2010-06-27
> **howefield said:**
> Glad you're sorted, I had to do the same.

Might be worth subscribing to this thread, the developer is active and has posted, so may get an update as to when/if sopcast will be made to work with VLC 1.1...

[http://ubuntuforums.org/showthread.php?t=1032901&page=42](http://ubuntuforums.org/showthread.php?t=1032901&page=42)

Awesome :)

---

### Post by Maestronaza on 2010-09-12
I've the same problem, can't open sopcast. Tried to uninstall vlc and sopcast many times...but I guess I can't really get rid of the newer vlc version.

Can I ask your help to solve this problem? 

Thanks in advance

---

### Post by bhishan on 2010-09-13
> **Maestronaza said:**
> I've the same problem, can't open sopcast. Tried to uninstall vlc and sopcast many times...but I guess I can't really get rid of the newer vlc version.

Can I ask your help to solve this problem? 

Thanks in advance

Go to Administration -> Synaptic Package Manager
Type vlc in the search box and then mark the vlc option for complete removal if it is higher than 1.1
It should work after that
I am using vlc 1.06 
But i still have one problem  When i click the sopcast link it doesnt open sopcast So i right click the sopcast link and click copy link Then I open sopcast click open and paste the link in the search box and open it It works that way
Hope this helped you :)

---

### Post by ilabor on 2010-09-15
[http://ubuntuforums.org/showpost.php?p=9847168&postcount=422](http://ubuntuforums.org/showpost.php?p=9847168&postcount=422)

---

### Post by howefield on 2010-09-15
> **ilabor said:**
> [http://ubuntuforums.org/showpost.php?p=9847168&postcount=422](http://ubuntuforums.org/showpost.php?p=9847168&postcount=422)

Thanks for that, seems to work for me.

---

### Post by howefield on 2010-09-15
> **bhishan said:**
> When i click the sopcast link it doesnt open sopcast

Try this

[http://maketecheasier.com/install-sopcast-in-ubuntu/2010/06/10](http://maketecheasier.com/install-sopcast-in-ubuntu/2010/06/10)

---


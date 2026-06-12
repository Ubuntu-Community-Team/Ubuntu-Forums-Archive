---
title: "vnc port change"
date: 2010-01-20
forum: Mythbuntu
---

### Post by davidstoll on 2010-01-20
In Mythbuntu, the vnc server is started on bootup.  I think you can change the port number via the command line, but how do I change the port number permanently (config file?) or using command line options on the automatically loading script?

i.e.
I want to permanently change the port number for the VNC server in Mythbuntu.

Thanks,
David

---

### Post by johnnybirdman on 2010-01-20
Good question.  Never tried... but went looking for the answer and think I found it here.
[[COLOR="DarkOrange"]**_http://ubuntuforums.org/showpost.php?p=4148896&postcount=3_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4148896&postcount=3")

Choice 1 should work.
J.

---

### Post by davidstoll on 2010-01-20
Unfortunately, 1 won't work because I'm not running gnome.  Mythbuntu uses the lightweight xfe.

The main problem with 2 is that it gets reset after a reboot.  He did link to a method for making it run at startup, but the vnc server is also running at startup.  So, if I'm going to change something at startup, I would prefer to make the right change.

However, I had not seen that post and I appreciate you looking for it.  I have done quite a bit of searching all over the place (in these forums and others) and I just haven't seen a direct solution to this question...yet.  ;)




> **johnnybirdman said:**
> Good question.  Never tried... but went looking for the answer and think I found it here.
[[COLOR="DarkOrange"]**_http://ubuntuforums.org/showpost.php?p=4148896&postcount=3_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4148896&postcount=3")

Choice 1 should work.
J.

---

### Post by johnnybirdman on 2010-01-20
I'm also running the stock xfe mythbuntu but I believe you can just
```
sudo apt-get install gconf-editor
```
and work it like that.
I'm not in front of my myth box right now so I can't confirm.
J.

---

### Post by davidstoll on 2010-01-20
So, this editor is more than just a text editor like gedit?  It is like some sort of (to use a windows term)...registry editor...in that it accesses configurations scattered around...or something?

I'll give it a try, but it's confusing that installing separate program allows me to change the port on a program that is already installed and running....see what I mean?



> **johnnybirdman said:**
> I'm also running the stock xfe mythbuntu but I believe you can just
```
sudo apt-get install gconf-editor
```
and work it like that.
I'm not in front of my myth box right now so I can't confirm.
J.

---

### Post by davidstoll on 2010-01-20
Ok, so it is like a registry editor.  Probably a poor comparison, but I get the drift.

Anyway, I don't have "remote_access". :(



> **davidstoll said:**
> So, this editor is more than just a text editor like gedit?  It is like some sort of (to use a windows term)...registry editor...in that it accesses configurations scattered around...or something?

I'll give it a try, but it's confusing that installing separate program allows me to change the port on a program that is already installed and running....see what I mean?

---

### Post by johnnybirdman on 2010-01-20
yes, very similar to regedit to use a windoze term.

However, there my be an xfe equivalent.  
try this at the command prompt

```
xfce4-settings-editor
```

Sorry I'm not at my myth box now or I would try and give you better help.
If you want to wait I'll check on this in more detail when I'm home, just a few more hours at the grind.

J.

---

### Post by davidstoll on 2010-01-20
Thank you johnnybirdman.  If you want to take a peak when you get home, that would be awesome.

It looks like this editor doesn't have a search function, so it's a bit of a treasure hunt, but I'm not seeing any sort of alternate port or VNC entry.  :(

I just cannot believe there isn't a conf file somewhere.


> **johnnybirdman said:**
> yes, very similar to regedit to use a windoze term.

However, there my be an xfe equivalent.  
try this at the command prompt

```
xfce4-settings-editor
```

Sorry I'm not at my myth box now or I would try and give you better help.
If you want to wait I'll check on this in more detail when I'm home, just a few more hours at the grind.

J.

---

### Post by nickrout on 2010-01-20
x11vnc is started by /usr/share/mythbuntu/session.sh

You can edit that file to change the options. Updates will probably rewrite it.

Or you could change mythbuntu's settings so that it doesn't automatically, and start it with your own options.

---

### Post by davidstoll on 2010-01-21
Oh, yeah!  That's it.

Now, is there a way to initialize this new port (or anything change in this file for that matter) without rebooting the computer?

Thanks!


> **nickrout said:**
> x11vnc is started by /usr/share/mythbuntu/session.sh

You can edit that file to change the options. Updates will probably rewrite it.

Or you could change mythbuntu's settings so that it doesn't automatically, and start it with your own options.

---

### Post by nickrout on 2010-01-21
for a one-off you could simply kill x11vnc and start it again with the parameters you want.

Actually killing X and restarting it should work too.

---


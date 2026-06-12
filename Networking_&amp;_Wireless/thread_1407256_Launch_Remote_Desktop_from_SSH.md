---
title: "Launch Remote Desktop from SSH"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by antwerp-avp on 2010-02-15
Hi, guys,

I have a home server with Ubuntu 9.10 installed. I connect to it by VNC. I have manage there System->Preferences->Remote Desktop service for that.

When this service is working I see its icon on the top panel.

From time to time I cannot connect by VNC. I notice that I can't see icon on the panel for some unknown reason. Why this service is quitting automatically? Can I launch it manually by SSH connection to that server?

I found in Web next solution: 

sudo gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

but it doesn't help for me.

Thanks.

---

### Post by suseendran.rengabashyam on 2010-02-15
Hi,

If you don't see an icon on top panel it doesn't mean that the Remote Desktop service is not running. By default, you might see the icon when somebody is connected to your computer but you can change the default behavior by going to System->Preferences->Remote Desktop and checking "Always display an icon".

Coming to your second question.. After you SSH to the machine, try the command

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

to enable Remote Desktop. No need to add "sudo" before the command.

I hope this helps.

---

### Post by antwerp-avp on 2010-02-15
Thank you for your response!

Yes I know about that option and it set as 'Always display an icon' for me. To resolve that problem I should launch 'Remote Desktop' again from System->Preferences. gconftool-2 command doesn't help me. I have try it with and without sudo.

Thank you.

---

### Post by antwerp-avp on 2010-02-16
Can anybody help me with that problem?

Thanks

---

### Post by suseendran.rengabashyam on 2010-02-16
Hi,

After you SSH to the machine, try the command

```
dbus-launch gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

```
to enable Remote Desktop

```
dbus-launch gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
```

to disable Remote Desktop

More details can be found in
[http://ubuntuforums.org/archive/index.php/t-266981.html](http://ubuntuforums.org/archive/index.php/t-266981.html)

I hope this helps.

---

### Post by antwerp-avp on 2010-02-16
Thank you! That's resolved my problem

---


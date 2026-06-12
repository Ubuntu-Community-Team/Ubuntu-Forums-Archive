---
title: "HOWTO Setup a networked printer with Windows"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by finlost on 2010-02-14
To begin, I am not a Ubuntu/Linux know-it-all.  In reality, I hardly know what I am doing.  I often spend hours of time trying to resolve issues or to add spiffs to my Ubuntu distro.  If you find errors in this post, please be kind and let's get it fixed so we are sharing quality information.

Tonight I decided to setup my HP1020 printer on my Ubuntu box and then shared the printer so I can print from my Vista laptop.  

I did a lot of Googling and searching on this forum.  Many were baffled by the lack of complete instructions on setting up a shared printer.  I had success by pulling from several sources.

[[COLOR="Red"]This is the first tutorial[/COLOR]]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") I attempted to use.  It was vastly incomplete.

First, install Samba.  I already had this on my Ubuntu box for file sharing.  (Two good links to get this running for file sharing - [[COLOR="red"]HOWTO Setup Samba peer-to-peer with Windows[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605") and [[COLOR="Red"]Clarification on Samba usernames[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6941704&postcount=785"))

Next I followed this tutorial, [[COLOR="red"]sharing CUPS printers[/COLOR]]("https://help.ubuntu.com/community/SettingUpSamba#Sharing CUPS Printers").  I performed the *graphical configuration* first without success as it couldn't find my printer.  

I then performed the *manual server configuration* as follows.

Bring up a terminal and paste the following

```
sudo /etc/init.d/samba stop
```

```
sudo gedit /etc/samba/smb.conf
```

In the *Global Section* of the smb.conf file, make sure it contains the following two lines.

```
   printing = cups
   printcap name = cups
```

In the *Printers Section* of the smb.conf file, copy and paste the following (remove or comment out the current "Printers" lines if they exist in your smb.conf file)

```
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

```

Save and close the smb.conf file.

Now back to the terminal to restart Samba

```
sudo /etc/init.d/samba start
```

You can close the terminal window as we are done in there.

I then went back and performed the *graphical configuration* and it found my printer.

The last step was to login to my Vista machine and find the shared printer.  There is plenty of information on the web to assist you with this so I don't think it is necessary to post those steps here.

I hope this helps those struggling with network printing.

[IMG]http://www.brews-bros.com/public/style_emoticons/default/cheers.gif[/IMG]

---


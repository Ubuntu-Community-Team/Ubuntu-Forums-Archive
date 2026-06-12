---
title: "Windows network drives won't map/mount"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by sw40c on 2009-09-29
I have a problem with mounting/mapping my Windoze network drives at work.  I am running Jaunty (9.10), with samba and all appropriate goodies.  I have searched the internet and these forums in vain and nothing has been able to help.  I did change settings in nsswitch.conf as in this [link]("http://ubuntuforums.org/showthread.php?t=1135842&highlight=windows+network+drive"), but still not luck.  When connected to my work intranet via both wireless and wired connections I cannot seem to access the drives.  All my Windoze mappings look something like this:

\\SfaXX\BLAHBLAH$

Under Places>Connect to Server I changed the service type to Windows share, called the server BLAHBLAH, placed \\SfaXX\BLAHBLAH$ on the share line, tried both username and domain/username with the username field, and placed my domain in the domain field.  I hit connect, it prompts me for my password, and after a few seconds says it cannot connect.  

Any ideas/suggestions or another GUI way I can connect with these resources?  Unfortunately it must be GUI as I need to access many files to complete my project and using the CLI would be a major pain.

Thanks in advance for any help!:(:(

---

### Post by srt4play on 2009-09-29
Maybe it was a typo, but in the server field you should put SfaXX not BLAHBLAH which is the share name.

Just re-read your post. The server field should contain SfaXX and the share line should contain BLAHBLAH$

---

### Post by Iowan on 2009-09-29
You may have already seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To, but it's worth a link - in case you haven't.

---

### Post by sw40c on 2009-10-06
Thanks all! I solved my problem thus:

[LIST=1]
[*]Pinged my share drive, sfaXX.mydomain.org, with CLI command
[*]Control-C to quit ping loop, copy IP to clipboard
[*]Open Connect to Server
[*]Paste IP in Server field
[*]Under share place folder name - XXX$
[*]Folder - leave blank
[*]Username - network logon username
[*]Domain - work domain
[*]Click OK
[*]Enter password - your choice if you want it saved
[*]Once mapped, bookmark drive
[/LIST]

That's it!

---


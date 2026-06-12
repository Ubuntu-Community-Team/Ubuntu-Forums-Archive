---
title: "Quick and dirty file transfer?"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by Sunships on 2012-01-11
Hi everyone,

I have two computers connected to the same wireless router. I want to download files/folders from the hard drive of one computer onto the other. Normally I would use a USB stick and just copy them over, but I am currently stuck without one. I don't want to go to the trouble of setting up anything as permanent or complex as samba (unless it has become vastly simplified in the last couple of years).

I have ushare running on the computer with the files, which I normally use to stream media to my XBox. I used to use Twonky for this, and recall being able to download files to other machines from the Twonky server through its web interface. Does ushare have a similar function, and if so, how do I use it?

Can I use ssh? If so, do I need to start ssh services on the computer with the files (if so, how?), and what commands do I use to perform the transfer?

Do I have any other simple options? 

Thanks for your help everyone :)

EDIT: The computer with the files I want is running 10.10. I forget which version the other machine is running, but think it is either 9.10 or 10.4.

---

### Post by prshah on 2012-01-11
> **Sunships said:**
> 
Can I use ssh? If so, do I need to start ssh services on the computer with the files (if so, how?), and what commands do I use to perform the transfer?

Practically any sort of file sharing requires you to install a server (software program) on at least one of the computers.

For quick file transfer, you can use: NFS, Samba, SSH (scp), FTP, etc, but each requires a "server" program to be installed.

For SSH, you need to install openssh-server (from repos, software center, apt-get) on any one machine. Make relevant config changes to "/etc/ssh/sshd_config" (usually only port number). Subsequently, copy to/from the machine use```

#examples - scp (Secure Copy Protocol / Secure file copy)
#scp -P 6765 somefile someuser@192.168.1.11:/home/someuser/somedir/
# scp - Secure Copy command
# -P 6765 (Port Number, default 22, must be same as defined in /etc/ssh/sshd_config
# somefile - file to copy
# someuser@192.168.1.11:/home/someuser/ - location to copy file

```

As long as you have ssh server running on any ONE machine, you can copy files TO and FROM the machine without the need for ssh server; you will only need ssh and scp (both available by default).

I personally recommend ssh/scp, since you can also use it with sftp (secure file transfer protocol) which most FTP clients also support.

As you get used to it, you can then add key authentication which means that preauthenticated computers will be allowed to transfer files to/from without the need of password to login.

---

### Post by Sunships on 2012-01-11
This sounds like exactly what I need.

I'm a little fuzzy on the syntax, but the wikipedia page on scp seems pretty clear. I'll post here again if I have any issues.

Thanks a lot prshah!

---

### Post by Lars Noodén on 2012-01-11
rsync over ssh is very good, too.  Especially if you have to make several tries at copying the data or just want to make a fast update.  rsync only copies the changes, not the whole file, so the second and subsequent times it is run, it is very fast.  Also, it uses ssh by default.

---

### Post by nothingspecial on 2012-01-11
If you run a ssh server on either machine you can do this with nautilus.

The methods are slightly different for each of your releases. As I am running 11.10, I'll outline how to connect to your older release **from** it.

Install openssh-server on the older release.

On your 11.04 box, open nautilus and click File > Connect to server. Fill in the details as in the screenshot exchanging my details for yours.

[ATTACH]210627[/ATTACH]


After the connection is established you will be able to browse the other computers entire file system and drag and drop folders/files from one to the other. An entry will appear in nautilus' sidebar starting "SFTP .....". You can right click that and choose to add a bookmark. From then on, every time you want to connect you just have to click the bookmark in the sidebar.

If you want to do it the other way around then the layout of the connection box is slightly different but the priciple is the same. It is accessed from the places Menu.

---

### Post by Sunships on 2012-01-11
Thanks nothingspecial - I may give your method a try first as I'm very lazy when it comes to the command line!!

Lars, rsync seems pretty cool, thanks - if this ends up being a regular thing then it could be very handy!

Thanks guys :)

---

### Post by Sunships on 2012-01-11
I'll try as many of these methods as I can in my lunchbreak. I'll mark the thread solved then, if I get any of them to work, but in the meantime any other suggestions are more than welcome. This is an area where I feel I am ready to learn more!

---

### Post by Sunships on 2012-01-11
Sweet. I am using nothingspecial's method and it is chugging along nicely. Very simple, job done. Thanks again, all.

---


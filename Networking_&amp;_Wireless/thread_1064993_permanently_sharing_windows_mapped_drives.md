---
title: "permanently sharing windows mapped drives"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by SteveHillier on 2009-02-09
I am getting closer and closer to shipping Ubuntu based workstations to my business users - but I have a little problem.
I have a Windows domain server.  I have shares on this server which are normally accessed by 
```
\\servername\sharename
```
On Windows I can map these drives so that drive s: points to the common(public) folder either by mapping in Explorer or in a script such as 
```
net use s: \\servername\sharename /switches
```
I have recently come across some software which is looking very interesting.  I have come across the configuration file for this which on Windows can be amended to 
```
pathname=\\servername\sharename\folder\subfolder
```
and with this I can now access the correct files (which were produced on an Ubuntu box) from a Vista client.
So things are looking up.  File created on the Ubuntu platform can be transferred to a Windows domain share and accessed from Windows client.
I have used the 'Connect to Server' GUI to connect the share which allowed me to transfer the data but doing this comes up with a title such as 'sharename on servername'
I need two more things to make this work nicely.
Firstly I would like to mount shared folder permanently on logon which would make it similar to my [net use] script.  I think there are ways for this but I have not found it together in one place yet.
Second I need to change the Linux configuration file to find this path.
I have tried 
```
pathname=//servername/sharename/folder/subfolder

```
and the above with trailing '/'
I have tried 
```
pathname=sharename on servername/folder/subfolder
and
pathname="sharename on servername"/folder/subfolder
```
I tried editing fstab to
```
//servername/sharename	/mountpoint	smbfs	users,credentials=/etc/creds 0 0
```
I have looked in /mnt but there is nothing there.
I must be missing a trick.
If I get there before any of you I will let this forum know first however....
As always, thanks in anticipation.

---

### Post by dutchman72 on 2009-02-09
Did you create the mountpoint folder before running the fstab command? If it isn't present, the mount wont show.

The other option is to use mtab.

Its located at /etc/mtab and command setup is, <file system> <mount point> <type> <options> <dump> <pass>. They are almsot exactly the same options you would use in fstab.

---

### Post by SteveHillier on 2009-02-09
> **dutchman72 said:**
> Did you create the mountpoint folder before running the fstab command? 
No, I didn't.
I will work on this tomorrow.
Many thanks

---

### Post by capscrew on 2009-02-09
> **dutchman72 said:**
> ...The other option is to use mtab.

...They are almsot exactly the same options you would use in fstab.

Do not modify the /etc/mtab file.  it is a list of currently *[COLOR="Red"]mounted[/COLOR]* file systems and is automatically created by fstab and will be overwritten at the next boot up.  See the bottom of the man page for details.

---

### Post by SteveHillier on 2009-02-10
> **dutchman72 said:**
> Did you create the mountpoint folder before running the fstab command? If it isn't present, the mount wont show.

Many thanks for this.  I now know what I have to do so solve an issue I have been pondering for some time.

I combined your comments with those I found elsewhere on the forum to get an almost perfect solution,  just a few tweaks left now.

For the benefit of others who might be new to this.

I created the mount point in terminal with 
```
sudo mkdir /mnt/mountpointname
```
then I edited fstab with gedit from the terminal
```
sudo gedit /etc/fstab
```
adding the line
```
//server/sharename  /mnt/mountpointname  smbfs user credentials 0 0
```
then in terminal I ran 
```
sudo mount -av
```

---


---
title: "Xubuntu Network Drives"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by buster2209 on 2012-09-11
I have 2 computers both running Xubuntu 12.04 that are connected to the same wireless network.  Computer 1 has 3 external drives attached to it.  I would like to access a specific folder on one of these drives from computer 2.

I know these computers can see each other through the wireless network as I can ping them

What's the best way to do this?  And what do I need to do?  Gigolo, Samba, gvfs, cifs, it's all very confusing...

Thanks in advance

---

### Post by Toz on 2012-09-12
If its just these two computers that you want connected and sharing, have a look at nfs. Install and configure nfs server on Computer 1 and connect to it from Computer 2. More information can be found here: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by buster2209 on 2012-09-12
> **Toz said:**
> If its just these two computers that you want connected and sharing, have a look at nfs. Install and configure nfs server on Computer 1 and connect to it from Computer 2. More information can be found here: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

Thanks for the reply.  I will try this tonight

---

### Post by Bucky Ball on 2012-09-12
I discovered Gigolo the other day and it rocks. It is already in Xubuntu in Apps>System (I only run Xubuntu and this is dead easy).

I also use Filezilla and Bareftp. Really easy also. Unison is great, too. It can sync folders between computers on the network. Cool.

Just make sure you have ssh installed to used Filezilla and connect using sftp. You will find all this easier if you have static IP addresses set for the two machines. That way there is no mistake.

I'd avoid Samba if not using Win machines. Clumsy and you don't need it. Other things do the job better, IMHO, for Linux.

---

### Post by buster2209 on 2012-09-12
> **Bucky Ball said:**
> I discovered Gigolo the other day and it rocks. It is already in Xubuntu in Apps>System (I only run Xubuntu and this is dead easy).

I also use Filezilla and Bareftp. Really easy also. Unison is great, too. It can sync folders between computers on the network. Cool.

Just make sure you have ssh installed to used Filezilla and connect using sftp. You will find all this easier if you have static IP addresses set for the two machines. That way there is no mistake.

I'd avoid Samba if not using Win machines. Clumsy and you don't need it. Other things do the job better, IMHO, for Linux.

I tried Gigolo but can't find any documentation on how to set it up.  Do you know of any?

---

### Post by Morbius1 on 2012-09-12
> I tried Gigolo but can't find any documentation on how to set it up.  Do you know of any?     For a general set up you can look at this:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

That mini HowTo was written specificity to access and then automout samba shares but the general set up is the same. To use it with SSH:

On one machine install SSH server:
```
sudo apt-get install openssh-server
```THen on the other machine use Gigolo to access it:
Gigolo > Actions > Connect > Service Type: SSH > Server:

For Server it can take may forms:
An ip address: **192.168.0.100**
A host name: **machineXYZ**
An mDNS qualified host name: **machineXYZ.local**

You don't have to put in the port or username - gigolo will figure out the port and it will ask you for credentials later.

There&#8217;s also another way to implement this so that machineXYZ-SSH shows up when you access "Network" in Thunar if you're interested.

** Just remember that without some advanced configuration SSH will allow at a minimum read access to your entire machine by the remote user so it is not in the same category as Samba.

** There is no NFS option in Gigolo. THere used to be a GUI for NFS once but Debian / Ubuntu pretty much abandoned it to focus on Samba since it's cross platform by default.

** Also, these "external drives" need clarification. If these are NTFS formatted USB drives then there may be an issue accessing them regardless of protocol since it will have you as the owner and access allowed only to you. Samba can be made to allow this sort of thing. I don't use NFS so I can't speak to that.

---

### Post by Bucky Ball on 2012-09-13
Gigolo? Create a bookmark using the IP of the other machine and the directory you want, eg: /home/your_user/Music, then connect to it ...

Your file manager will open to the folder you have designated on the other machine, just like any other. You will also see the share listed in the left side pane like a local partition/drive:

sftp://192.168.0.*** ...

... etc, or whatever your IP is.

---

### Post by Morbius1 on 2012-09-13
If we are going down the SSH path let me offer the following for your dining and dancing pleasure. The true power of Gigolo comes from having remote shares auto mount at login. If that is not a requirement and since all your machines are running Xubuntu there is a way to make this more seamless.

** Make sure you install openssh-server on your machine.
** Create a user on your machine corresponding to the remote user unless you want the remote user to login as you.
** Then make it possible to announce that service to everyone on the local network:

Create a file as root:
```
gksu leafpad /etc/avahi/services/ssh.service
```And add this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h SSH</name>
<service>
<type>_sftp-ssh._tcp</type>
<port>22</port>
</service>
</service-group>

```Save the file.
When the other machine's user opens up Thunar he should be able to go to Network and see "Machine-name SSH".

---

### Post by Bucky Ball on 2012-09-13
Nice work Morbius1. 

One thing; Gigolo doesn't mount anything at boot for me. If I want to mount a network share with Gigolo I need to do it manually everytime. Maybe there's some default setting to get it running as a service at boot. ;)

---

### Post by Morbius1 on 2012-09-13
Gigolo should automount at login if you:

** Select "Auto Connect" when creating the bookmark.

** And add gigolo to your start up applications. 

In Xubuntu: Menu > Settings > Session and Startup > Application Autostart > Add > gigolo

In Ubuntu: Dash thingy ( can you tell I'm an XFCE user ;) ) > Startup Applications > Add > gigolo

[COLOR=Blue]**EDIT**[/COLOR]: You should also set gigolo's preferences to start minimized: **Edit > Preferences > Interface> ****"Start minimized in the Notification Area"** and **Disable "Show auto-connect error messages"**

---

### Post by Bucky Ball on 2012-09-13
Cheers, but have no use for any auto-mounts at boot and avoid running anything I don't need at startup (pared back Xubuntu). I generally only ever need to fire up Filezilla and dump a directory and that's it so don't need anything running in background. Useful info for others though ... ;)

---

### Post by buster2209 on 2012-09-13
Morbius, boom!  That is exactly what I wanted; a simple way of sharing network drives on Xubuntu.

I do have one more question though, I am unable to edit any file on the network drive from the client computer.  How can I make the files writable?

---

### Post by Morbius1 on 2012-09-13
Accessing a computer remotely via SSH is exactly like having that remote user login locally. The linux permissions of the thing you are sharing has to allow the other user read write access. So what are the permissions of the folder you are sharing:

```
ls -dl /path/to/shared/folder
```

---

### Post by buster2209 on 2012-09-13
> **Morbius1 said:**
> Accessing a computer remotely via SSH is exactly like having that remote user login locally. The linux permissions of the thing you are sharing has to allow the other user read write access. So what are the permissions of the folder you are sharing:

```
ls -dl /path/to/shared/folder
```

I am unsure.  I am not at my Xubuntu machine right now.  I assume you want me to execute this code from the machine running the SSH server?  What permissions should it be?  777?

---

### Post by Morbius1 on 2012-09-13
> **buster2209 said:**
> I am unsure.  I am not at my Xubuntu machine right now.  I assume you want me to execute this code from the machine running the SSH server? 
Yes I want you to run that command from the SSH server
>  What permissions should it be?  777?You know, the answer to that question can get to be very complex depending on what your definition of "write" is.

** A chmod 777 will allow anyone to add and remove files from a folder.
** What it will not do is allow anyone to edit a file within that folder.

If the remote user .. say agnes ... adds a file to a folder it will save as: owner = agnes and permissions of 664. Agnes can edit the file but everyone else can only read. 

There's a way to modify permissions by setting up a group ( or using an existing one like plugdev ), making both users members of that group, setting the group of the parent folder to that group, and then setting the setgid bit to make sure that all future files added to that folder inherit that group. Then when agnes adds a file it will save with owner = agnes, group = plugdev, and permissions of 664. Every member of the plugdev group will be able to edit that file.

So it would go something like this:

** Add agnes to the plugdev group:
```
sudo gpasswd -a agnes plugdev
```Change group ownership of the shared folder:
```
sudo chown :plugdev /path
```Change permissions to allow all members of the plugdev group access and set the setgid bit:
```
sudo chmod 2770 /path
```The "2" is the setgid" bit and it will make all new files inherit the group.

[COLOR=Blue][I]You could also make it this:
```
sudo chmod 3770 /path
```That will add the "sticky bit" ( 1) that will block a user from deleting files he does not own to the setgid bit ( 2 ).[/I][/COLOR]

Like I said it can be a complicated answer and depends on what you mean by "write".

---

### Post by buster2209 on 2012-09-13
I'll clarify; I want any machine to be able to copy, cut, and paste to the network folder as well as every user to be able to edit any folder and/or file in the network folder.

---

### Post by Morbius1 on 2012-09-13
Then you need to go through the setgid routine adding agness or any other user you have to the plugdev group.

[COLOR=Blue]*There is another method using bindfs but that can be a bit of a mind bender if you've never seen it before. **The setgid method is the classic Linux way of doing this sort of thing.*[/COLOR]

---


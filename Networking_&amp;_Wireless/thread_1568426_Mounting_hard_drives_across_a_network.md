---
title: "Mounting hard drives across a network"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by Shawn K on 2010-09-05
My wife and I have separate desktops, both running Ubuntu 10.04.  We're both connected via ethernet cable to our home network.

Our eventual plan is to buy her another computer, and at that point her existing one will become the network hub for a HTPC setup.

What I'm trying to figure out right now is how to configure my computer to see and mount her hard drives across our network.  Since her box had more HDD space than mine, I want to be able to access that drive, create folders as I see fit, and use it as if it were physically installed in my PC.

Ideally, I'd like to see her HDD in my Places folder as a mounted device and access through the GUI.

At first I thought I'd have to use Samba, but it sounds like that's more for accessing Windows machines from Linux clients.  I installed SSH server side to my wife's PC, but I'm not sure if that's going to give me the interface I want (I don't want to be forced to only use command line), and I don't think I'm using it correctly, since I couldn't get anything to connect.

I'm in the dark here, and learning about network operation for the first time.  Am I making it too hard for myself?  Is there an easier way to do this?  Can anyone give some advice or point me to some links so I can learn more about this?

---

### Post by Morbius1 on 2010-09-05
> At first I thought I'd have to use Samba, but it sounds like that's more for accessing Windows machines from Linux clients.It's was actually developed so that Windows clients could access UNIX file servers. Smbclient ( on a linux client ) is for clients to access Samba servers. In a peer-to-peer network a given machine can be both.

You could try Samba first. For the majority of users it will work out of the box. But when it doesn't work it will take years off your life span to determine what's wrong and how to fix it. Besides the NFS'ers and the SSH'ers will post things like "I told you so" and "real men don't use samba in an all Linux network"

Anyway, if you want to try it here's the easiest way:

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
[COLOR=Blue]*If you don't have samba installed it will ask you if you want to install it - you do.*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

If the samba and networking gods are smiling upon you today the other box will show your documents share in their Nautilus under Networks.

---

### Post by Shawn K on 2010-09-05
Hmmm.  I ended up installing Samba and configured the folder sharing permissions as you said.  I did the same thing on my wife's computer with a sample file.

In Places on my computer, I can see a "network" icon now, and when I open it I see my wife's computer and mine (plus a folder labeled "network").  When I try to open anything, though, I get an error message saying "Failed to retrieve share list from server".

When I tried to click on the Network tab on my wife's start list, I get "Could not display 'Network:///'  Error: Location is already mounted.  Please select another viewer and try again."

It would appear that the Samba gods are not smiling on me today.

Now what?

(Remember that this is my first foray into networking of any kind.  Be gentle.)

---

### Post by Morbius1 on 2010-09-05
You know this is beginning to wear me down. There are just too many bugs in too many places.
> "Could not display 'Network:///'This part of the error ususally means the one or both of two packages are not installed. You might run the following commands from a terminal to make sure they are installed:
```
sudo apt-get install gvfs-fuse
sudo apt-get install gvfs-backends
```The problem is I have never seen it next to the following phrase:
> Location is already mounted.I don't even know what that means. If it's mounted then show it to me.

> "Failed to retrieve share list from server"This has happened before but not with the kind of regularity that seems to be happening with 10.04. it could be many things ... firewalls, misconfigured shares, the network itself ...

Can you access the shares by ip address. In a terminal type:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the other box.*[/COLOR]

If you can then bookmark it: In Nautilus > Bookmarks > Add Bookmark

---

### Post by drdos2006 on 2010-09-05
I found this more than useful.
Server software on one machine, client software on the other.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 


regards

---

### Post by Shawn K on 2010-09-05
Morbuis1 - Sorry, didn't mean to wear you down.  :)

I noticed that when I tried to access Preferences ==> Personal File Sharing, I couldn't select the "share public files on network" button because it was missing a few of the packages.

A little research took me to this thread:

[http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)

It appears that I was missing two Apache packages.  When I installed them, everything started working.  Go figure.

(Now why would Ubuntu only give you some of the packages needed for a function that it has installed by default?  Seems like a bit of an oversight.  But anyway...)

So now I've learned how to see both computers across the network, and I've learned that whatever I need to access needs to be put in the $HOME/public folder.

I know what I **can** do, now I want to see if I can make it do what I *want* to do.  Can I make this file sharing work for *all* folders, not just whatever is in $HOME/public?  

Ideally, what I want to do is install an extra HDD in my wife's case, and then access *all* of it without restriction, with full read/write priviliges, and have it mounted as an extension of my own file system.  

I have a second HDD in my case that is nothing but a WinXP install with some PC games installed.  I can see it on my Places => Computer screen and mount/unmount is as desired.  *That's* what I want to do with whatever additional HDD's I put in my wife's case.

---

### Post by Morbius1 on 2010-09-05
Just so you know , "Personal File Sharing" is not Samba. It's another method entirely using a baby apache file server which broadcasts it's shares using avahi. 

You haven't fixed samba you're using something that can only share one folder and that's your "Public" folder.

> Can I make this file sharing work for *all* folders, not just whatever is in $HOME/public?   No.

[COLOR=Blue]**Edit:**[/COLOR] I never thought about this before because I'm one of the 12 people on earth that can use Samba out of the box, but maybe you can create a symbolic link to the Public folder.
[COLOR=Blue][B]
Edit2:[/B][/COLOR] I thought an example would be helpful. Let's say you wanted to share your Music folder. To create a symbolic link to your Public folder you would do this :
```
 ln -s /home/your_user_name/Music /home/your_user_name/Public
```

---

### Post by Morbius1 on 2010-09-05
o

---

### Post by Shawn K on 2010-09-05
I had to look up what you meant by a "symbolic link".  Is that the same as a "soft link"?

I've briefly read some things about "hard links" and "soft links", but while I think I understand the concept, I don't understand the value in one over the other if they both ultimately do the same thing.  However, that's another topic for another thread.

Tell me if I'm understanding you correctly.  It sounds like you're saying that:

* "Personal File Sharing" isn't really designed to do what I'm wanting to do.
* I need to learn how to use Samba to do what I *want* to do.
* I could do a workaround (of sorts) to deal with PFS's limitations by making symbolic (soft?) links to all of the folders that I wanted to share, but that sounds a little laborious.

Do I have it right so far?

EDIT:  I followed the NFS Server/Client link that Drdos2006 posted, but it sounds like NFS isn't doing anything fundamentally different than what Personal File Sharing is doing for me already.  Is this an accurate assessment?

---

### Post by Morbius1 on 2010-09-06
Personal File Sharing ( PFS ) is just another method ( like samba, nfs, ssh , etc ) of sharing files. There are a half dozen HowTo's on the web - one of them in this forum - that thinks its Samba. All of them are wrong. If it works for you and if symbolic links can work with it then you'll have almost the same functionality as Samba or NFS. Symbolic links in Samba do not work without a hack but since PFS is not Samba it might work with PFS. 

The big difference is authentication and the kind of control you can have over the share. PFS allows you to password protect or not password protect the Public Share. Samba and NFS allow you to create a mixture of shares that allow guests to access some shares and only one person or group to access others. If your intent is to create simple shares that anyone in your home network can access then PFS may be all you need.

---

### Post by Shawn K on 2010-09-06
Maybe I should explain what my ultimate goal is.

The long-term goal I have is to build a home theater network (for use in the living room) that also has several clients throughout the house that aren't home theater-centric (my office, my kid's room, my workshop, etc.).  The seemingly logical first step in my mind was to learn Home Networking 101 and how to access files across our network.

My wife's current desktop will serve double-duty (for the near future) as both her desktop and the network hub, but eventually we'll get her another stand-alone client PC and her current PC will become solely a network hub with large storage.

My desire to mount the additional HDD across the network is because eventually, I want all of the media portion of our network on a single independent drive.  That drive will (eventually) be accessed by XBMC or some other front-end software (for the living room), or will be accessed by various other playback programs on the other clients (like Rhythmbox, VLC, etc.).

I had just assumed that to work in the way that I want it, I'd have to learn how to mount the entire drive across the network.  Am I making it more complicated than it needs to be?  Are you saying that I could essentially make a symbolic link (or series of them) that ties the entire additional HDD to the /public folder?

What's the BEST (from a technological standpoint) way to do this, and what's the EASIEST way?

I sure appreciate you walking me through this process.  Thanks for your help so far.

---

### Post by Morbius1 on 2010-09-06
I take it you didn't try a symbolic link in Personal File Sharing. If you had you'd have noticed that is doesn't work. At least not for me but PFS has always been kind of flaky for me.

So that means nfs, samba, or ssh.

You don't care for ssh and samba doesn't work on your system or network so that leaves nfs. I personally don't use nfs so I can't be of any help but it sounds like drdos2006 can.

---

### Post by Shawn K on 2010-09-06
You're right, I hadn't tried that symbolic link.  I just forgot about it in the course of discussion.  Sorry about that.

I tried it just now, and it didn't work for me either.  It said that the Public file didn't exist (which it does).  I tried changing the file path to several other folders besides the Public folder, but I keep getting the same error message.

Any idea *why* Samba wasn't working for me, or is it the kind of thing that I need to have years of post-graduate study to understand?

---

### Post by addison.merchut on 2010-09-06
I do this by using [**sshfs**]("http://en.wikipedia.org/wiki/SSHFS"). What I do is  mount a directory on to my laptop from my computer downstairs: check [**this**]("http://www.go2linux.org/sshfs-mount-remote-filesystem-using-ssh") out . I can then play (edit, delete, copy, paste, or move) the media on my laptop just fine. The only real constraint is how fast your local internet is, IE your wireless hardware.

Now this works pretty well for me, but I have been wondering if there's a better way to do this but I haven't found anything yet (plus this is secure).

Let me know what you think.

---

### Post by aytech on 2010-09-09
Hi, 
Not sure if thats what you want, I have a drive in the network and i mount it like this: 
1. Create a folder and name it, say, Share ( I created it in home folder)
2. In terminal, type: [FONT=monospace]
[/FONT]***smbmount [I]//smb/share* /home/user/Share -o username=*smbusername*, password=**[I]**smbpassword**

[/I][/I][I]As a result the shared drive appears as local folder and you'll see additional HDD in My Places. I use it to sync the files with the network share. 

I believe a script can be created to do this automatically every time you log on, but I dont know how to do it, trying to find the info, still new to Ubuntu myself ;)
[/I]

---

### Post by Hobgoblin on 2010-09-09
> **Shawn K said:**
> Maybe I should explain what my ultimate goal is.

The long-term goal I have is to build a home theater network (for use in the living room) that also has several clients throughout the house that aren't home theater-centric (my office, my kid's room, my workshop, etc.).  The seemingly logical first step in my mind was to learn Home Networking 101 and how to access files across our network.


You don't say if all these systems will be using Linux.

If they are then I would go with NFS, instructions for setting it up can be found in the [server guide](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html).  Just don't forget to install nfs-common on your clients.;)

If some will be using Windows then use Samba or a mix of NFS and Samba (which is the way I have done it on my own network).

---

### Post by Shawn K on 2010-09-12
> **Hobgoblin said:**
> You don't say if all these systems will be using Linux.

Yes, they will all be using Linux (Ubuntu).  Eventually, the living room client will have XBMC installed.

> If some will be using Windows then use Samba or a mix of NFS and Samba (which is the way I have done it on my own network).

I've tried the Samba route a couple of times now, but I can't make the damn thing work *at all*.

I have a new problem now, too.  I had PFS working just fine (at least from a simple file sharing standpoint) until a couple days ago.  Now, when I go to Places > Network, it takes an unusually long time to respond, and it doesn't see my wife's computer anymore (however, her computer sees mine just fine).

I've double-checked all of the permissions and made sure all of the appropriate boxes were checked, and everything looks like it's supposed to.  The only visual difference that I've noticed is that the double-arrow icon that I used to see over shared folders is no longer present on either my wife's or my computers.

Why she can see my computer but I can't see hers is a mystery to me.  Is this a known bug in 10.04?

**EDIT:**  Doggone it, now PFS is working correctly.  This on-again, off-again thing with PFS is starting to get on my nerves.  Is there something about networking that I need to learn yet to make this stable, or is PFS just naturally buggy?

---


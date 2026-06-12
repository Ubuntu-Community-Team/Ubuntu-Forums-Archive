---
title: "Lucid and Samba  - here we go again [rant]"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by whistlerspa on 2010-05-13
Been using Ubuntu since 5.04. Love 10.04 as a desktop  - unbeatable but same old same old when it comes to file sharing. Set up the Samba service to get (yet again)[using 64Bit]

Unable to mount location - Failed to retrieve share list from server

I once went through hours of command line gibberish to try and get this going (with only limited success), but can't be *****ed to do that again. 

After all this is 2010. If Linux is to be a serious contender for replacing Windows it really need to get past this. 

Doubt there's an easy fix - can anyone prove me wrong? :(

---

### Post by wilee-nilee on 2010-05-13
> **whistlerspa said:**
> Been using Ubuntu since 5.04. Love 10.04 as a desktop  - unbeatable but same old same old when it comes to file sharing. Set up the Samba service to get (yet again)[using 64Bit]

Unable to mount location - Failed to retrieve share list from server

I once went through hours of command line gibberish to try and get this going (with only limited success), but can't be *****ed to do that again. 

After all this is 2010. If Linux is to be a serious contender for replacing Windows it really need to get past this. 

Doubt there's an easy fix - can anyone prove me wrong? :(

**_Yes Ubuntu isn't meant to usurp MS_**. When you describe the command line gibberish I suspect your having problems; that maybe somebody who knows how to do this can help you with. I have never used a file sharing setup in other then a virtual setup, so I can't help, but others probably will in spite of the rant, if your lucky.

Do you really think it's Ubuntu's fault or is it a misunderstanding of what makes it work?

---

### Post by Grenage on 2010-05-13
> After all this is 2010. If Linux is to be a serious contender for replacing Windows it really need to get past this.

Oh?  Where is MS' support of file sharing in Linux?

That aside, I have had no issues sharing folders using only the GUI; _exactly_ what are you trying to do?

---

### Post by whistlerspa on 2010-05-13
What I mean by 'gibberish' is that I'm able to copy and paste command lines into terminals as per support forums advice and do so to install Medibuntu for example, for every distribution that I install. 

However I've never really had the time or inclination to learn what all that means. 

It would be nice if the Ubuntu development team could focus on making file share setup easier and less buggy to do.

---

### Post by whistlerspa on 2010-05-13
> **Grenage said:**
> Oh?  Where is MS' support of file sharing in Linux?

That aside, I have had no issues sharing folders using only the GUI; _exactly_ what are you trying to do?

I'm trying to get file shares to work so that I can share between my Ubuntu Laptop and desktop.

---

### Post by Grenage on 2010-05-13
You don't normally need to use the terminal to share a folder in Ubuntu, You can use the GUI.

In Nautilus, right-click a folder and select *Sharing Options*.

---

### Post by Morbius1 on 2010-05-13
Can you access the remote shares by ip address:

Open up a terminal and type** nautilus smb://192.168.0.100**
[COLOR=Blue]*Change 192.168.0.100 to the real ip address of the remote machine.*[/COLOR]

If you can then "Bookmark" it. In Nautilus > Bookmark > Add Bookmark.
It will show up under "Places" and you can make believe that it's a Windows "mapped drive"

---

### Post by whistlerspa on 2010-05-13
> **Grenage said:**
> You don't normally need to use the terminal to share a folder in Ubuntu, You can use the GUI.

In Nautilus, right-click a folder and select *Sharing Options*.

Yes did all that -on the desktop I can see the folders that I've shared on that machine but the laptop gives the error message.

---

### Post by fuzz500 on 2010-05-13
Agree. And can't prove you wrong. 

Can't get two Lucid clean installs to see each other with simple nautilus file sharing... samba is "unable to retrieve share list from server". What's with that?

While there is much to get excited about with Ubuntu, there are several long running bugs that should be fixed. Networking with windows shares should be completely automatic... like it or not Windows is still Goliath, and you have to play nice with it. Also, there are a couple of Nautilus bugs that **** me off from version to version. I can't turn off "keep aligned" for desktop icons, and another thing: I want to be able to move icons right into the corners of the screen. Nautilus bumps it from the edge with a margin every time. Sigh. I'm back to google searches and RTFM. 

Fuzz.

---

### Post by JoeEndUser on 2010-05-13
I agree, I did get it working in Lucid, but I had to reboot my modem/router and every computer on the system as well as follow Dmizer's guide at the following [http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve")

It's so less aggravating when I take a deep breath and remember I get all this good stuff for nothing.

If it weren't for Visual Basic and DRM...

Cheers

---

### Post by JoeEndUser on 2010-05-13
Correction: I'm not really sure if it was necessary to reboot everything, after I did, I went back to Problem 3 in the guide above and I had entered the wrong thing in the nsswitch.conf file.

---

### Post by whistlerspa on 2010-05-14
Still no luck - I'll have to continue using flash drives to share files from machine to machine I guess - it's really irritating though :confused::mad:

---

### Post by whistlerspa on 2010-05-14
> **Morbius1 said:**
> Can you access the remote shares by ip address:

Open up a terminal and type** nautilus smb://192.168.0.100**
[COLOR=Blue]*Change 192.168.0.100 to the real ip address of the remote machine.*[/COLOR]

If you can then "Bookmark" it. In Nautilus > Bookmark > Add Bookmark.
It will show up under "Places" and you can make believe that it's a Windows "mapped drive"

This link reminded me why I swore that I'd never stuff around like that again - sorry not this one!

---

### Post by whistlerspa on 2010-05-14
> **JoeEndUser said:**
> I agree, I did get it working in Lucid, but I had to reboot my modem/router and every computer on the system as well as follow Dmizer's guide at the following [http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve")

It's so less aggravating when I take a deep breath and remember I get all this good stuff for nothing.

If it weren't for Visual Basic and DRM...

Cheers

I meant this link!

---

### Post by craig100 on 2010-05-14
I have no problem with Ubuntu/Windows sharing. The problem I always have is Ubuntu/Ubuntu sharing!!!  It's totally daft that it doesn't work right out of the box!  I have Karmic on my laptop and have just put Lucid on a new PC.  The laptop can see the PC but the PC can see neither the laptop nor itself.  It's ridiculous that a "normal" user has to go farting about with loads of commands line stuff when all he wants to do is share files. What's so "techy" about that, nothing!  I don't care what's behind it all, I just want it to work. I use Ubuntu to get stuff done, not to play with Linux.

I've installed Samba and NFS and set directories up for sharing but it still doesn't work.

Is anyone aware of a decent trouble shooting article on this as the Ubuntu help isn't.

Cheers,

Craig

---

### Post by odius on 2010-05-14
Yeah I've never been happy even with a crossover cable, however this is how I'm transferring files...right now.

I have:
a laptop wireless to a linksys wrt300n
a desktop wireless to the same router

I have tried to use 192.168.101 etc which did not work for me
what does work is knowing the machine name. So from my desktop I go to Nautilus | File | Connect to Server : select "Windows Share" and in "Server" enter my laptop name which happens to be "laptop"

I don't see any icons in Network before or after this, however a windows pops up containing the icons, the behavior if deff strange 

Hope this helps

---

### Post by craig100 on 2010-05-14
Thanks Odius, that did it.

How ******* stupid!  This sort of thing is now BASIC to owning more than on machine, which a lot of people do.  It needs sorting out FAST or the masses won't tolerate it!

Thanks again, it's got me going for now;)

Cheers,

Craig

---

### Post by whistlerspa on 2010-05-14
Connect to Server IP addressing works desktop to laptop but not visa versa. makes no sense to me both are set up identically.

Could it have something to do with the wireless connection security I wonder?

---

### Post by whistlerspa on 2010-05-14
> **whistlerspa said:**
> Connect to Server IP addressing works desktop to laptop but not visa versa. makes no sense to me both are set up identically.

Could it have something to do with the wireless connection security I wonder?

Apparently not just tried a cable connection to the laptop and same result - so it's totally random.

---

### Post by Eiríkr on 2010-05-15
Hey there folks --

Just thought I should chime in here and note that Samba was and is pretty much required for sharing from a Linux / Unix-y machine to a Windows machine, but it is neither required nor necessarily optimal for sharing between Linux / Unix-y machines.  A number of people in the Ubuntu package selection chain have opted to use Samba where it might not really belong...

FWIW, I've had much better performance using NFS for sharing between Unix-y machines.  This *does* require some CLI (command-line interface) work, but **any** serious mucking about on *any* OS will require a certain amount of obscure operations.  (CLI, meet Registry... <shudder.>)

Anyway, if you're on a home network, sharing between Unix-y machines, **please** give NFS a thought.  It's a couple years old at this point and was written for sharing from Ubuntu to a Mac, but [post=4387032]this post[/post] goes over the basics of NFS shares and handling user and group ID mapping between machines.  

Meanwhile, if you'd really like to give Samba a try, have a look [post=4694000]here[/post], and read through the rest of the thread and the linked threads as well.

I understand everyone's frustration with the complexity of these issues, but it bears noting, the simple fact remains that file sharing between different operating systems is, by its very nature, **complex**.  Considering as well that "Windows" actually means something more like half a dozen different OSes still in use (2K, various flavors of XP, Server 2008, Vista, 7, and relevant SPs to boot), you've got a very large and moving target to try and hit.  Sadly enough, there's just no easy way to simplify all of this.  

That said, these issues *can* be conquered, if you're willing to spend the time and energy to learn.  If so, great!  Those of us here on the Forums are more than happy to pitch in and answer your questions as best we can.  

Cheers,

-- Eiríkr

---

### Post by whistlerspa on 2010-05-15
Thanks Eirikr for your contribution to this thread. I personally don't want to go through all that command line stuff as I said in my first post but others may find it useful.

As an aside I've now found that if I disconnect wireless to my laptop on boot and use a cable connection I can now share folders with my desktop. This means that it's the wireless connection that is causing the problem. How to fix that I don't know.

---

### Post by whistlerspa on 2010-05-15
Now it'ds decided to start working LOL - IP address leasing issue maybe?:confused:

---

### Post by SeanONe on 2010-05-27
Why has ubuntu broken smb sharing? This is the standard way of sharing files in the world. It does not work under lucid and is broken. The "help" is always some idiot waffling on about how it's a feature not a bug. It's a total failure of a second rate OS, pure and simple.

---

### Post by ardvark on 2010-05-27
I, also, have been fighting these problems. I may be off base here, but my impression of this problem- "Unable to mount location - Failed to retrieve share list from server", could be a turned off service on your Windows PC. I have two Windows PC's and one Linux box on my home network. I was always wondering why when the second Windows box was turned off I would get the above error. It looks like the windows network info is stored on each PC, if this service is running, so Ubuntu is just trying to read this info from at least one of the Windows PC's.
On WIndows -> Control Panel -> Admin Tools -> Services (extended)

I don't remember the actual service name, I was using a trouble shooting procedure for XP...

---

### Post by johnh10000 on 2010-06-13
lucid is just plain weird.  You have to install bits of apache for reasons unknown.

[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

this was working for me, then yesterday it all stopped AGAIN.

Is there a distru where this acctually works?

---

### Post by Morbius1 on 2010-06-13
> **johnh10000 said:**
> lucid is just plain weird.  You have to install bits of apache for reasons unknown.

[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

this was working for me, then yesterday it all stopped AGAIN.

Is there a distru where this acctually works?
95% of the information on the web concerning Samba is just plain wrong. Case in point is the above link:
> Ubuntu Lucid steps

The above is only half of the equation. Now we have to properly configure Ubuntu for sharing. The most obvious step is to go to System -> Preference -> [COLOR=Blue]Personal File Sharing [/COLOR]and click the top choice “Share public files on network”:News Flash: Personal File Sharing is not Samba. This is what Personal File Sharing is:
> The program is meant to run in the background when the user is logged
    in, and when file sharing is enabled a webdav server is started that
    shares the $HOME/Public folder. The share is then published to all
    computers on the local network using mDNS/rendezvous, so that it  shows
    up in the Network location in Gnome.The author of the HowTo also makes another mistake: There are two completely different ways of using samba to create shares and the author is using both at the same time on the same target - insanity:

[COLOR=Blue]Nautilus-shares[/COLOR] which create share definitions in /var/lib/samba/usershares: Nautilus > Right Click a Folder > Sharing options.
[COLOR=Blue]
Classic-shares[/COLOR] which create share definitions in /etc/samba/smb.conf: System -> Administration -> Samba

The HowTo is a mess. Granted, 80% of the information in this forum concerning Samba is wrong also but the advantage of this forum is peer review. If I say something just plain out stupid ( and lord knows I have ), there are 20 other members that will instantly correct me.

---

### Post by mbuotidem on 2010-06-15
> Anyway, if you're on a home network, sharing between Unix-y machines, please give NFS a thought.

Yeah, i am on a home network and trying to share files between several Ubuntu computers. I've tried SAMBA and it didn't work so where can i get NFS? I checked in software center but im not sure that what i saw there is what i need.

> News Flash: Personal File Sharing is not Samba. This is what Personal File Sharing is:
Quote:
The program is meant to run in the background when the user is logged
in, and when file sharing is enabled a webdav server is started that
shares the $HOME/Public folder. The share is then published to all
computers on the local network using mDNS/rendezvous, so that it shows
up in the Network location in Gnome.

I tried to use this method but i am told: "this feature cannot be enabled because the required packages are not available on your system" there is no hint as to where i can get the required packages! Does anyone have an idea what these required packages are? 


Morbius1, you are obviously knowledgeable about SAMBA. It would be nice if you could write a tutorial on it, both how to use it to share to windows clients and to Ubuntu clients cause, we newbies honestly need help! :confused:

---

### Post by Morbius1 on 2010-06-15
> **mbuotidem said:**
> I tried to use this method but i am told: "this feature cannot be enabled because the required packages are not available on your system" there is no hint as to where i can get the required packages! Does anyone have an idea what these required packages are? 

You need to install the following packages:
[B]Apache2.2.bin
libapache2-mod-dnssd[/B]

Please note that it will allow you to share only one folder: **/home/username/Public** and it doesn't work very well which is why I think Ubuntu ships this thing disabled. Maybe you can get it to work.

> Morbius1, you are obviously knowledgeable about SAMBA. It would be nice if you could write a tutorial on it, both how to use it to share to windows clients and to Ubuntu clients cause, we newbies honestly need help! :confused:Thanks for the compliment but I'm not knowledgeable about Samba I only sound like I am :wink:

Here's the problem with Samba. There are two parts to Samba - share creation and share recognition. The share creation part is simple and if you use Nautilus-share here's my HowTo:

Right click on a folder you own
Select "Sharing Options"
Select all three boxes
Select "Create Share"
Done.

It's the Share Recognition part of Samba that causes so many people grief. For the majority of people it works out of the box but for some it does not. There are HowTo's out there that address this part of the problem and it can get involved and some of them are actually accurate. I once fixed someone's samba share recognition problem by replacing his  router with another make and model and without making any changes whatsoever at the OS level.

I for one have never had a problem with the backend regardless of what linux distro I've used.

---

### Post by mbuotidem on 2010-06-16
i finally succeeded in sharing files between my ubuntu systems. I didn't use SAMBA although i will try it out in my leisure. I used a utility called gshare. It did everything very simply for me.:guitar: 

If you are trying to share files, gshare may just help you.you should try it. and the great thing is that its help is comprehensive.

@morbius, i installed those dependencies and the option became available and i also succeeded in sharing the files using it(the built in file sharing option that ships with Ubuntu). :guitar:

:confused:The problem i am currently having with my samba is that i have no users and i am unable to add users!:confused:

I have attached a screenshot. Even when i create and add users, they do not appear! I wonder why. I would like to get samba to work because I need to share my printer with a windows pc. 

How do i solve this problem?

---

### Post by Morbius1 on 2010-06-16
mbuotidem,

The only problem with gshare, which creates an FTP server and uses avahi to broadcast it's share to the network, is that a Windows client needs to have bonjour ( the windows version of avahi ) installed. Of couse you may already have bonjour installed if you have iTunes installed on it. Another interesting "all linux" possibility is the utility "Giver" which uses an IM-like process to share files.

It's interesting that you got "Personal File Sharing" to work. For me, Windows would see the share for a brief moment and then disappear. For a Linux client it would be able to access the share and 5 minutes later the share would disappear. 

As for the Samba part ( and this is pure rant so be forewarned ) is that you're using GADMIN. That utility is a Systems Administrator's tool and for a home network it's almost guaranteed to take a very simple default smb.conf and turn it into an incoherent mess - the network equivalent to spaghetti code. You might want to start a separate topic and post your smb.conf and other things by posting the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s 

```

---

### Post by mbuotidem on 2010-06-16
I guess you are right. I saw someone saying something about gsambad and how it messes up things. Gadmin may be doing exactly what gsambad does. so do you have any idea how i can revert to the default samba configuration? Also, inplace of gadmin, which other simpler samba application exists? 


I know this sounds dumb, but im gonna ask anyway, for giver to work, it must be installed on the two systems right?

anyway, as you said, i will start a separate topic and post the results of those commands. thanks

---

### Post by Morbius1 on 2010-06-16
> do you have any idea how i can revert to the default samba configurationThere is a copy of the default smb.conf file located at /usr/share/samba/smb.conf that has one error in it. So to revert to the original configuration here's what I would do:

In a Terminal:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```[COLOR=Blue]*This will create a copy of the current smb.conf and call it smb.conf.bak*[/COLOR]
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```[COLOR=Blue][I]This will copy the other smb.conf to the correct place for Samba to funcion.
[/I][COLOR=Black]To correct the error:[/COLOR][/COLOR]```
gksu gedit /etc/samba/smb.conf
```Look for the following line:
> encrypt passwords = noand change no to yes
> for giver to work, it must be installed on the two systems rightYes, which is why it can't be used with windows since there is no Windows giver app. There is no Apple giver app either.
> inplace of gadmin, which other simpler samba application exists? If your needs are simple: Nautilus itself - Right click a folder > Sharing Options.
If your need are more complex: system-config-samba
If your needs are very complex and you know what you're doing ( or you've deluded yourself into thinking that you know what you're doing as I have :wink: ) : gedit

---

### Post by ardvark on 2010-06-16
I had to use several threads to finally get things to work. The first was to make sure I could ping between all PCs using both IP and PC name. To get that to work I had to add LMHOSTS to the windows PC and HOSTS to my Linux box. Another thread discarded the smb.conf file that GADMIN produced and I made a new one with the following entries:

[global]

workgroup = HOME
netbios name = linux1
encrypt passwords = yes

[homes]
path = /home
read only = no
browseable = no

[media]
path = /home/roku
browseable = yes
read only = yes
public = yes


The media share is for my Roku media player. I share a printer that's on the Windows PC. If your printer is on the Linux PC then I believe you have to have some more entries to get Windows to access that printer. Also after setting up this smb.conf file and if it works, if you go back to GADMIN it will try to modify this file, don't let it...

---

### Post by Garthhh on 2010-06-17
> **whistlerspa said:**
> Been using Ubuntu since 5.04. Love 10.04 as a desktop  - unbeatable but same old same old when it comes to file sharing. Set up the Samba service to get (yet again)[using 64Bit]

Unable to mount location - Failed to retrieve share list from server

I once went through hours of command line gibberish to try and get this going (with only limited success), but can't be *****ed to do that again. 

After all this is 2010. If Linux is to be a serious contender for replacing Windows it really need to get past this. 

Doubt there's an easy fix - can anyone prove me wrong? :(

I'm adding this thread to the list below:

There are also some other related threads:
Paddy Landau's thread
[http://ubuntuforums.org/showthread.php?t=1491092](http://ubuntuforums.org/showthread.php?t=1491092)
with a work around

Wolfrage's better solution:
[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

A bug [please subscribe]:
[https://bugs.launchpad.net/ubuntu/+s...ba/+bug/592610]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610")

My thread from a couple of weeks ago:
[http://ubuntuforums.org/showthread.php?t=1491180](http://ubuntuforums.org/showthread.php?t=1491180)

The community of developers has spent many hours developing this   capability, too bad it doesn't work, without a bunch of fiddling around   on the command line:confused:
If you are reading this & would like to be able to share files with a   couple of mouse clicks, post a comment on the threads & especially   the bug

---

### Post by Morbius1 on 2010-06-18
> **Garthhh said:**
> 
The community of developers has spent many hours developing this   capability, too bad it doesn't work, without a bunch of fiddling around   on the command line:confused:
I'm not disagreeing with you that Samba can be problematic for some ( but not all users ) but Samba was not created for linux users to network Windows / Linux machines in their home network. Samba in fact was not originally created for linux at all but for UNIX files servers in a corporate network comprised of Windows clients. Samba works pretty much as designed in that environment.  

Here's one example of how the focus of Samba is on the enterprise and not on the home network. By default the following line is set as this:
> name resolve order = lmhosts wins host bcastThis parameter determines how samba will resolve machine names on the network. In an enterprise environment bcast ( or broadcast ) is disabled because if you have hundreds of windows clients broadcasting their presence on the network it would bring the corporate network to it's knees. In a home network lmhosts, wins, and host are either empty or  non-functional. bcast is the only one that works and it's listed last. That's why changing the priority of that line by placing bcast first often ( but not always ) resolves the name recognition problem:
> name resolve order = bcast lmhosts wins host As for a bug report on Samba, I'm not altogether sure that will resolve anything. If you look at what's happened to it:
> [Chow  Loong Jin]("https://launchpad.net/%7Ehyperair")             wrote             on 2010-06-14:                                                             [  #3]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610/comments/3")                                                        Looks more like a name resolution and  presence detection issue more than a configuration issue, so I'm  reassigning to samba.Ubuntu passed it to Samba. I'm guessing Samba doesn't consider anything broke - the user has just mis-configured something. Who's the user here - me or Ubuntu itself. We're in an infinite loop.

---

### Post by Garthhh on 2010-06-18
> **Morbius1 said:**
> I'm not disagreeing with you that Samba can be problematic for some ( but not all users ) but Samba was not created for linux users to network Windows / Linux machines in their home network. Samba in fact was not originally created for linux at all but for UNIX files servers in a corporate network comprised of Windows clients. Samba works pretty much as designed in that environment.  

Here's one example of how the focus of Samba is on the enterprise and not on the home network. By default the following line is set as this:
This parameter determines how samba will resolve machine names on the network. In an enterprise environment bcast ( or broadcast ) is disabled because if you have hundreds of windows clients broadcasting their presence on the network it would bring the corporate network to it's knees. In a home network lmhosts, wins, and host are either empty or  non-functional. bcast is the only one that works and it's listed last. That's why changing the priority of that line by placing bcast first often ( but not always ) resolves the name recognition problem:
As for a bug report on Samba, I'm not altogether sure that will resolve anything. If you look at what's happened to it:
Ubuntu passed it to Samba. I'm guessing Samba doesn't consider anything broke - the user has just mis-configured something. Who's the user here - me or Ubuntu itself. We're in an infinite loop.

I'll go through the whole thing from scratch, following instructions as I get them from the GUI & see where it gets me
I just walked into the other room & sat down at an ol Pentium III pc that is hooked to my printer.  I added Mint9 [last week] to this PC, because it's easier to use than 10.04 using the graphical interface.  I can generally stick to using software from the manager & synaptic.  I update usually within a few hours of when I notice there is a notifications.
I went to my home folder & right clicked documents, clicked share options
got asked for permission [root I guess], gave it
told I needed other packages & was asked if wanted to install the packages to do windows shares, clicked install
Samba & lib-something[dependency] installed
I filled in the share popup
the icon now shows an outstretched hand
went to my other computer I don't see any other computers on the network?
I go to network & click through the menus, don't see anything that appears to be relevant
I go to system[control center in mint] click Personal file sharing & get a message 
"this feature cannot be enabled Because the required packages are not installed on your system"
I go to help, which says 
I should go to startup preferences
I scroll through the list & see that personal file sharing is enabled
at this point I'm at an impass, so 
I go have a look at synaptic & type personal file sharing into search, no results
change to file sharing, 65 results
I scroll through the list & see 9 of them are already installed
File
Gnome-user-share
Giver
Samba Common
Libwclient
Samba Common-bin
Samba Client
Samba
I'll stop here for the time being at least on the PC which has not had a bunch of stuff installed

at the very least the help file & or on screen prompts should lead you to successfully sharing 1 folder, it should be a little more difficult to share the entire home folder just for security sake

It's a shame to be so close & not go the rest of the way with graphical method of file sharing that doesn't require finding information through searching here or the rest of the internet.
this basic task should be described adequately on help or through prompts/error messages within the process of right clicking a folder.

I understand that when you deal with the intricacies of an operating system on a day to day basis, it can be difficult to look at things with the eyes of a newbie
Let me know if there is any way I can help? :) 

I just posted the above on the bug report

---

### Post by brion@cbkidder.com on 2010-06-18
I am having the same frustrations and it is infuriating. What is so hard about getting an Ubuntu machine to share files with a Windows machine on a workgroup?

The point is we shouldn't HAVE to play around in Nautilus. We should be able to click the icon that says NETWORK and browse the files on our network.

Grenage and wilee-nilee, your comments are not helpful. If you don't have a solution to suggest, don't reply ok?

My Windows machines can see the workgroup MYGROUP and can share files between them, but not with the Ubuntu machine.
My Ubuntu machine can see the workgroup MYGROUP but only shows itself as a member of it and can't see the other machines or their files.

I love Ubuntu, and am working very hard to stay off Windows for good but nonsense like this makes it impossible.


1. If I click Network, I see:
network:///
WINDOWS1
WINDOWS2
UBUNTU3
Windows Network

2a. If I double click either Windows1 or Windows2, the header changes to smb://windows1/ or smb://windows2/ and says nothing is in the share, even though I know there is because I share files between these two Windows machines using the same shares.

3a. If I then click on Windows Network from step 1, I see:
smb:///
MYGROUP

3b. If I double click MYGROUP, it only shows my Ubuntu machine. If I double click that I see its own shares.

4. If I go to Terminal and type nautilus smb://192.168.1.6
The error message is:
Could not display smb://192.168.1.6
Error: Failed to retrieve share list from server
Please select another viewer and try again.

This all is on a clean install of Lucid by the way. Any suggestions would be appreciated.

---

### Post by JoeEndUser on 2010-06-18
For a month from March through April, I worked with a good person on this forum to resolve his issues/my issues with Samba. Some of the things gleaned from four pages of posts are:

1. Disable the firewall (suggest either install gufw or use in terminal: sudo ufw disable)

2. You may need to reshare shares or reboot your windows machine after disabling firewall.

3. double check that you are pointing smb to the right ip address. Type ifconfig in terminal and note the address.

4. Try using the gui in Places - connect to server - select Windows Share as the service type. then put in the ip address in server you can leave everything else blank.

5. I found dmizer's guides (ubuntu staff) to set-up and fix to be brilliant (already mentioned in this thread), it did not work for others (already mentioned in this thread).

Unfortunately, with Lucid, fixing Samba in dmizer's way breaks Rhythm Box's network access - there is a conflict with Winbind. I would like to check out the music store some day, but right now file sharing is more important.

---

### Post by JoeEndUser on 2010-06-18
Sorry, No. 3 is wrong. That should be go to Start - Run in Windows type cmd, type ipconfig in the terminal window.

---


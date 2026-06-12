---
title: "trying to have a folder share automatically on reboot of ubuntu machine"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by ijason on 2011-06-10
greetings.

apologies if this is covered in another thread. after a good bit of searching i finally decided to start a new thread, but maybe i missed the answer!

i have an ubuntu machine with a folder that i typically share to the rest of the workgroup. even though i've set it up as a shared folder in System > Admin > Shared Folder, i still have to right-click on the folder and set the Sharing Options every time i reboot the machine.

surely there is a way to auto-share the folder on boot? all of the documentation i've found is people trying to auto MOUNT shared network folders from other machines, or trying to share VB folders... nothing that quite explained what i'm trying to do.

thanks!

/running 11.04

---

### Post by Morbius1 on 2011-06-10
> even though i've set it up as a shared folder in System > Admin > Shared Folder,
That sounds like Classic Samba Shares
> i still have to right-click on the folder and set the Sharing Options every time i reboot the machine.
That sounds like Samba Usershare.

2 different methods of using Samba to share files. Please post the output of the following commands:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by ijason on 2011-06-10
> net usershare info --long
[lr-downloads]
path=/home/livingroom/Desktop/Downloads
comment=
usershare_acl=Everyone:F, 
guest_ok=y

and
> 
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum windows limit (16384)
processing section "[printers]"
processing section "[printers]"
processing section "[LR-Downloads]"
loading services file OK.
Server role : Role_standalone
[global]
server string=%h server (samba, ubuntu)
map to guest=bad user
obey pam restrictions = yes
pam password change = yes
passwd program = /user/bin/passwd %u
passwd chat = blah*
unix password sync = yes
syslog = 0
log file = /var/log/samba/log.%m
dns proxy = no
usershare allow guests = yes
panic action /usr/share/samba/panic-action %d

blah*

[LR-Downloads]
path=/home/livingroom/downloads
read only = no
guest ok = yes

i retyped this manually, as i couldn't figure how to copy and paste through the remote desktop to that machine :< please ignore typos or capitalization errors, as they are likely mine. 

*blah denotes a long string that didn't seem pertinent so i left it out :) thanks for helping

---

### Post by Morbius1 on 2011-06-10
net usershare info --long
> [lr-downloads]
path=/home/livingroom/Desktop/Downloads
comment=
usershare_acl=Everyone:F, 
guest_ok=y                      What makes you think that that has to be reshared every time you boot?

If it's missing the share emblem that's a known bug that is not likely to get fixed anytime soon. The next time you reboot run the "net usershare .. " command again to verify that the share is present.

BTW, you have the same name on 2 shares that point to 2 different folders:
path=/home/livingroom/Desktop/Downloads
path=/home/livingroom/downloads

I personally would get rid of the one in /etc/samba/smb.conf. Even if they point to the same folder it's not a good idea generally to use 2 different methods to share the same target folder.

---

### Post by ijason on 2011-06-10
well, i've rebooted the ubuntu machine, and indeed "net usershare info --long" returns the same output as before. and the icon on the desktop wears the two arrows to indicate it is shared.

currently, i can't browse to it from my laptop, but that may be a different issue, as ubuntu computer doesn't even show up on my network neighborhood.

i agree about not sharing two different ways, is there a preferred method? either the 'right-click' or the System > Admin > Shared Folder... although both seem to need to be done for it to show up.

also, if on future rebooting of the ubuntu machine the share is not there, is there a way to edit the fstab or samba conf file to ensure the folder is automatically shared?

thanks for your time!

---

### Post by Morbius1 on 2011-06-10
I have never - and I mean never - had a shared folder unshare itself. I have never ever seen a post on that sort of thing happening. There are a couple of things that could happen that makes it look like it's unshared:

From the server the share emblem disappears for no apparent reason but you can always check with a net usershare if that happens.

From the client the whole darn machine disappears from the network. There are also a couple of bugs that deal with services not starting or starting in the wrong order so before doing anything drastic check to see if everyting is running:
```
sudo service nmbd status
sudo service smbd status
```If any are not running start them:
```
sudo service nmbd start
sudo service smbd start
```As for which method is preferred it really doesn't matter. I use both depending on the machine I'm working on but since all your shares so far allow guest access I would recommend the Nautilus method. For one thing every time you create a share the classic way or even edit smb.conf you have to restart the samba service. When that happens the whole network has to reset itself and it could take several minutes for everybody to settle down and become usable again. 

With Nautilus sharing it's all done without resetting any services.

---

### Post by ijason on 2011-06-10
interestingly... or, unfortunately, have some weirdness going on in a different way.

from the ubuntu machine, i can brows the network neighborhood and navigate to the shared folder on my laptop. from my laptop, when i brows the network neighborhood and then click to go onto the ubuntu machine i get this error :

> //LIVINGROOM-UBUNTlivingroom-ubuntu server (samba, Ubuntu) is not accessible. you might not have permission, etc.

clearly the network connection is working, as i am able to remote desktop to the ubuntu machine, and i'm able to brows my laptop from it. i haven't figured out how to make the ubuntu machine request credentials from me.

---

### Post by ijason on 2011-06-10
> As for which method is preferred it really doesn't matter. I use both depending on the machine I'm working on but since all your shares so far allow guest access I would recommend the Nautilus method. For one thing every time you create a share the classic way or even edit smb.conf you have to restart the samba service. When that happens the whole network has to reset itself and it could take several minutes for everybody to settle down and become usable again. 

by 'nautilus method' you're referring to simply right-clicking on the folder i want to share and setting it's Sharing Options? and you would suggest that i go into System > Admin > Shared Folders and remove the reference to the same folder, to prevent the computer trying to share the location twice?

---

### Post by Morbius1 on 2011-06-10
>                               //LIVINGROOM-UBUNTlivingroom-ubuntu server (samba, Ubuntu) is not accessible. you might not have permission, etc.                      Well there's a problem right there. "livingroom-ubuntu" is 17 characters long. It can only be 15 characters long - you can see how even the error message is attempting to truncate the name. It's one of those rules that we as users are supposed to just know I guess. The easiest way to correct this is through Samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
netbios name = lr-ubuntu
```[COLOR=Blue]*It doesn't have to be "lr-ubuntu" but is has to be 15 characters or less*[/COLOR] [COLOR=Blue]*in length*[/COLOR]
Then save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Then wait about 5 minutes for the network to calm itself.

> by 'nautilus method' you're referring to simply right-clicking on the folder i want to share and setting it's Sharing Options?Yes, it relies on a package called nautilus-share and It does a lot of the work for you regarding permissions and things and all of it automatically.
> and you would  suggest that i go into System > Admin > Shared Folders and remove  the reference to the same folder, to prevent the computer trying to  share the location twice?           That's what I would do. I like to keep things as simple as possible.

---

### Post by ijason on 2011-06-10
ah... it took rebooting both machines to refresh the netbois name to the truncated one, and then i could connect fine to it. 

i will assume that the issues i have had with the shares needing to be re-shared after a re-boot may have been flukes? or user error? or related to trying to share them through two different methods, and consider this thread closed.

thank you for your help :)

---


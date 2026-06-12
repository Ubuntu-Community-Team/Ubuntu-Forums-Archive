---
title: "Connecting three Ubuntu computers together."
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Boneyard on 2009-09-02
I have searched the forums, and found lots of problems releted to connecting windows to linux but few about connecting linux to linux, so it looks like i have a weird problem.

I have 3 computers, Aspire one netbook running Ubuntu and linpus, Aprire 5315 laptop running ubuntu and an old pc thats running ubuntu that i am going to use as a media server.

OK here is the problem, (i am an ex windows user so apologies for being thick, i just refuse to use windows anymore) my netbook can see the itself, the laptop and the old PC and another file called 'windows network' just fine when i click 'network' under 'places' and i can happyly stream video from any shared folder. My laptop will only display 'windows network', and not see any of the other computers. when i click 'windows network' it shows 'workgroup' and then if i click that, it says its 'unable to mount location'

i used the same install software on all the computers and did the same thing, what could prevent the laptop from seing the other linux machines? there is no firewall or anything like that i have tried the old turn-it-off-and-on-again trick...

command line stuff is a total mystery to me, I have no idea how you guys remember it! any help you can give would be amazing thank you.

OH I forgot to mention, I can remote desktop in to the old pc from the laptop, it works just fine

---

### Post by stinger30au on 2009-09-02
bound to be something simple like a config file incorrect or samba missing

the easiest way to get the machines talking is to install and run samba

sudo apt-get install samba

do this from shell, get this via applications, accessories, terminal

if your running 9.04 on all 3 its even easier, just use giver

sudo apt-get install giver


[http://code.google.com/p/giver/](http://code.google.com/p/giver/)

---

### Post by Boneyard on 2009-09-02
Thank you for the help, Samba is installed (i did what you suggested) and the problem remains. I also found a program called SMB4K and when i run it i can see all 3 computers, the old pc is listed in another colour (light blue) where the others are listed in black (not sure if thats relevant)

still, when i click places, network nothing has changed.

Anything else i can do?

########

OK I thought I would be clever and uninstall samba, then re-install, incase some config file was corrupted... nope, still the same after I re installed it (i used the package installer)

---

### Post by Boneyard on 2009-09-02
Ok a small update 

If i type the address (for example smb://terry-netbook/) in the window after it fails to find anything, I can see the shares! BUT this only works for my net book and the laptop.

So to summarise:

Netbook: can see everything, and be seen by everything
Laptop: Can see itself and Netbook, only if the address is typed in
Old PC: Can see everything, only if typed in

Its SO weird! When I hit 'Places > Network' on the Laptop, I dont see any computers other than 'Windows Network' But if I do it on the Netbook I can even see the wife and kids Windows based laptops!

It must be some weird config file, but as i have done nothing different to the other machines I am really, truely stumped!

:confused:

########

OK after a bit more fiddling, I think it could have something to do with 'workgroup' can I find out what workgroup the Laptop is in?

#######

OK Forget that, i read that it doesnt matter... why do i get this " Unable to mount location, Failed to retrieve share list from server" when I click on 'workgroup' but there is another domain (brockhill, its my sons school laptop) and if i click there i see his computer and can even get asked for a password?

This is driving me insane now...

---

### Post by Iowan on 2009-09-02
" Unable to mount location, Failed to retrieve share list from server"
This error reportedly has to do with firewall settings. 

I have a Samba server set up, and it works for Linux-Linux machines, but NFS is reportedly a more native (better?) way. [Here]("http://ubuntuforums.org/showthread.php?t=249889") is a How-To - if you'd like to investigate.

---

### Post by Boneyard on 2009-09-04
Thank you for that, Im fiddling with NFS now, but I am REALLY out of my depth!

I tried entering the IP into the address bar (smb://192.168.1.1 for an example) and it works fine!

I get Icons, clickable that shows all the shares! 

Confused? BOY am I!! :confused:

Thanks again for the help!

---


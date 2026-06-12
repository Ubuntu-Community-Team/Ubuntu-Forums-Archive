---
title: "[Tool for testers] Know your repositories"
date: 2010-10-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Framli on 2010-10-12
Hi fellow testers!
I test compulsively development releases since Karmic Alpha2. A frequent issue I encounter, with all the repos I tend to add, is never knowing when PPA and other repos are available for Ubuntu+1 and being confronted to ugly 404 bugs while updating.

I've just hacked a bash script to let us know when the repos we use support the release we are testing :
[https://code.launchpad.net/~davidc3/+junk/repostory](https://code.launchpad.net/~davidc3/+junk/repostory)

Use this command in a terminal to get the code:
```
bzr branch lp:~davidc3/+junk/repostory
```
The script will be in the "repostory" folder in your Home, so you have to go there and make the file executable:
```
cd repostory && chmod +x repostory
```
Make sure you have the curl and zenity packages:
```
sudo apt-get install curl zenity
```
That's it, you can now launch the script by either clicking it or typing:
```
./repostory
```

To get the latest changes, if you have a previously downloaded version just type:
```
cd repostory && bzr pull
```

[IMG]http://img831.imageshack.us/img831/3640/repostoryscreencast.gif[/IMG]

Your thoughts?

---

### Post by caryb on 2010-10-12
Sorry for the DFU comment but can you give some more detail on how to use this? This is what I get from the terminal...

bzr branch lp:~davidc3/+junk/repostory
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 1 revision(s).                                                                                                                                                
cary@stinkpad:~$ 


Cary

---

### Post by toobuntu on 2010-10-12
Actually, all you need to do is download the shell script he uploaded there. You can do that with:
```
wget -c http://bazaar.launchpad.net/%7Edavidc3/%2Bjunk/repostory/download/davidc%40framli.eu-20101012075452-6hyox9g00k9mv0pc/repostory.sh-20101012075410-vz0rt6o6h23eyd1h-1/repostory.sh -O ${HOME}/Downloads/repostory.sh
```

To use it, don't forget to make it executable and be sure you have curl and zenity installed.
```
chmod +x ${HOME}/Downloads/repostory.sh ; sudo aptitude install curl zenity
```

Then it's just a matter of double-clicking on it in your file browser and agreeing to "Run" it or putting this in your terminal:
```
${HOME}/Downloads/./repostory.sh
```

I suppose it should be mentioned that this is a GUI app and requires Xorg.

---

### Post by autocrosser on 2010-10-12
Nice tool---THANKS!!!

---

### Post by ubunterooster on 2010-10-12
Thanks a ton! This will be a great timesaver!

---

### Post by JOHNNYG713 on 2010-10-12
:guitar:Very handy!! Thanks!

---

### Post by DougieFresh4U on 2010-10-12
I thought that 'aptitude' wasn't in Meerkat or Natty any more? As I had to change the one command with 'aptitude' in it to 'apt-get' and all was good
Thanks

---

### Post by cariboo on 2010-10-13
Aptitude isn't installed by default. but it's still available in the repositories

---

### Post by Framli on 2010-10-13
Thank you all for your great feedback! I will update the first post accordingly.

[QUOTE=toobuntu]I suppose it should be mentioned that this is a GUI app and requires Xorg.[/QUOTE]
I thought that the screencast was pretty self explanatory about this, but you're right and I will update the script today to work with a "-nox" argument.

---

### Post by peepingtom on 2010-10-13
This is really useful, thanks a lot!

---

### Post by Framli on 2010-10-13
First post updated. Added a first draft of a cli only version.

---

### Post by davideotape on 2010-10-13
I like this :D

---

### Post by Vanishing on 2010-10-13
Nice tool..This is gonna save me  a BUNCH of time..:)
thanks mate

---

### Post by donniezazen on 2010-10-14
Thanks. What does those brackets around yes and no means.



Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Framli on 2010-10-15
The brackets mean that I'm experimenting with ways to show which version of the ppa you are using.

...and from your screenshot, I can see there is a problem with my script's interpretation of the dropbox repo and some other stuff.

If you have weird results, please provide screenshots, I will look into it.

---

### Post by karmila on 2010-10-16
Thanks, really useful tool!

Now, I can change my repo from maverick to natty as soon as it is available. No more need to check manually to ppa page each time.

---

### Post by plun on 2010-10-16
> **karmila said:**
> 

Now, I can change my repo from maverick to natty as soon as it is available. No more need to check manually to ppa page each time.

A button which starts software-properties-gtk would be nice to add....

---

### Post by karmila on 2010-10-16
> **plun said:**
> A button which starts software-properties-gtk would be nice to add....

And automatically change the distribution to natty :)

---

### Post by jerrylamos on 2010-10-16
> **cariboo907 said:**
> Aptitude isn't installed by default. but it's still available in the repositories
I was at Maverick Beta on two pc's - then apt-get mangled kernel update and I had to re-install both.  Nothing worked.  Fix broken packages they wouldn't even boot that far, chroot, you name it, they were dead.

Update manager has mangled things for me as well.  It said "Partial Upgrade", I looked at the package that was singled out and said I don't use that package.  Blam!

sudo aptitude update, sudo aptitude safe-upgrade hasn't done that to me.  It's on Lucid but I apt-get install aptitude on Maverick.

This is a natty that I used aptitude to install whatever it thought was safe.  Still running, famous last words.

Jerry

---

### Post by plun on 2010-10-16
> **karmila said:**
> And automatically change the distribution to natty :)

Even better....;)

---

### Post by ronacc on 2010-10-16
I'll add my thanks also .

---

### Post by ubername on 2010-10-17
Nice.

Seems to be a problem with the way it's counting available repo's. It says '3 of the 8' but has yes's against 6 of the 8.

---

### Post by Framli on 2010-10-17
Thanks everyone for your feedback, screenshots like this are really useful, there is indeed a mess I'm trying to solve with non-launchpad repos.

About automatically changing sources.list to natty when available, I will look into it once non-launchpad repos will be handled gracefully. But I'm still not sure I want to do this : if something breaks after going to natty on a repo, automatizing it will make it harder to track the source of the problem.

---

### Post by Framli on 2010-10-22
New update to the branch today. The "status" feature is slowly making it's way into the interface. No big change for now, but an "experimental" branch will open soon, for the brave.
It still doesn't provide useful info for dropbox, dl.google and maybe some others non-launchpad repos.

Please provide any non-launchpad repos you have in your sources. Thanks! :)

---

### Post by cariboo on 2010-10-22
For repositories that aren't maintained by Ubuntu,  you'll have to wait for them to catch up, in the meantime, use the maverick repositories. There won't be a lot of changes until after UDS-N which ends on the 29th of October.

---

### Post by afrodeity on 2010-11-18
offtopic, but what tool did you use to make the gif?

---

### Post by Framli on 2010-11-18
For gif screencasts, I use Byzanz, from the repos.
For people following the branch, the project is far from being abandoned and enhancements are slowly making their way into the script. More to come newt week. =)

---

### Post by dino99 on 2010-11-18
Many thanks David

that's such idea makes our experience easier, you rock :)

---

### Post by fil0~ on 2010-11-18
Great and helpful tool! It has saved me a lot of time. 
Thanks!

---

### Post by Izziedee on 2011-04-12
I had the same response. Despite the message, I found a repository directory had been created for me (do a "ls -lrt" at the command line). cd to that directory and continue with the rest of the instructions.

---


---
title: "Synergy not working at all."
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by Chris Richard on 2011-07-01
Before anyone wastes time reading this entire thread, I would suggest that if you actually have this problem, skip to the second page and look for my post titled RESOLVED. It may save you a ton of wasted time.

Okay, I had this posted a couple of days ago, but no responses and I've totally changed the configuration too, so I came back in to edit the entire post.

The problem: Can't get Synergy working at all.

The set up:

Three computers on a Belkin LAN, all on Ethernet.

Two clients running Windows XP SP3, and Synergy 1.3.1. 

The Syngery server is a triple boot Mac Pro running OS X Snow Leopdard, Windows XP (new install, not yet completely updated, and Ubuntu 11.04. Each OS is on a separate drive.

Synergy version on both OS X and Windows on the server is 1.3.1.

I have no idea what the synergy version is on Ubuntu. I don't know how to check it. I do know that newer synergy versions don't like to play nice with older versions.

I have been here:

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

I didn't look much further than the instructions for Quicksynergy, because I found the remainder of the page very unclear and confusing.

Quick Synergy did not  work at all.

I did take a look here though:

[http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/)

and his instructions, though they seemed easier to follow, didn't work either. I realize Matt's instructions are probably outdated.

When I first followed his instructions, I was able to get past the screen where the file "synergy.conf” is created, and I end up in a screen that looks like this:

[IMG]https://lh4.googleusercontent.com/-pv3_CI9dSUA/ThCrj9n48zI/AAAAAAAAAGs/y4y36mq6Q78/s512/edit-window.png[/IMG]

(except that the original screen showed the file name being edited at the bottom. This screen shot doesn't show that, because I can't get to that original screen anymore, for reasons explained below)

Matt's instructions then show the text to go into synergy.conf, but when I start typing "section" I get this instead:

[IMG]https://lh5.googleusercontent.com/-yTSDc1A8xCs/ThCrgIKkkLI/AAAAAAAAAGk/R-A31q5FG60/s512/edited.png[/IMG]

As you can see, nothing appears in the screen when typing "section:" until I type the "n" and that shows up in the second line.

So I tried it again, but this time it appears the first attempt already created a file, because I now get this screen right after entering:

```

sudo vi /etc/synergy.conf
```

[IMG]https://lh3.googleusercontent.com/-95GrwiCNGOM/ThCrj1VTGYI/AAAAAAAAAGw/vvNDKg8afWM/s512/file-exists.png[/IMG]

I don't know how much of this has to do with my inexperience with Linux, and how much might have to do with outdated instructions. Synergy documentation (for all versions out there) is sadly lacking and most of it is at least a couple of years old.

Can *anyone* shed any light on this for me? Without Synergy running, Ubuntu is missing the last critical feature I need on it to be of any use to me.

Thanks.

BTW: I realize many forums discourage or don't allow bumping. I hope the mods will realize the only reason I'm bumping this is first, because it got no responses at first, and second, the entire contents of this OP is now changed.

Thanks again.

---

### Post by Chris Richard on 2011-07-03
Bump. Reason: Entire contents of OP is changed.

---

### Post by apollothethird on 2011-07-03
> **Chris Richard said:**
> Okay, I had this posted a couple of days ago, but no responses and I've totally changed the configuration too, so I came back in to edit the entire post.

The problem: Can't get Synergy working at all.

The set up:

Three computers on a Belkin LAN, all on Ethernet.

Two clients running Windows XP SP3, and Synergy 1.3.1. 

The Syngery server is a triple boot Mac Pro running OS X Snow Leopdard, Windows XP (new install, not yet completely updated, and Ubuntu 11.04. Each OS is on a separate drive.

Synergy version on both OS X and Windows on the server is 1.3.1.

I have no idea what the synergy version is on Ubuntu. I don't know how to check it. I do know that newer synergy versions don't like to play nice with older versions.

I have been here:

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

I didn't look much further than the instructions for Quicksynergy, because I found the remainder of the page very unclear and confusing.

Quick Synergy did not  work at all.

I did take a look here though:

[http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/)

and his instructions, though they seemed easier to follow, didn't work either. I realize Matt's instructions are probably outdated.

When I first followed his instructions, I was able to get past the screen where the file "synergy.conf” is created, and I end up in a screen that looks like this:

[IMG]https://lh4.googleusercontent.com/-pv3_CI9dSUA/ThCrj9n48zI/AAAAAAAAAGs/y4y36mq6Q78/s512/edit-window.png[/IMG]

(except that the original screen showed the file name being edited at the bottom. This screen shot doesn't show that, because I can't get to that original screen anymore, for reasons explained below)

Matt's instructions then show the text to go into synergy.conf, but when I start typing "section" I get this instead:

[IMG]https://lh5.googleusercontent.com/-yTSDc1A8xCs/ThCrgIKkkLI/AAAAAAAAAGk/R-A31q5FG60/s512/edited.png[/IMG]

As you can see, nothing appears in the screen when typing "section:" until I type the "n" and that shows up in the second line.

So I tried it again, but this time it appears the first attempt already created a file, because I now get this screen right after entering:

```

sudo vi /etc/synergy.conf
```[IMG]https://lh3.googleusercontent.com/-95GrwiCNGOM/ThCrj1VTGYI/AAAAAAAAAGw/vvNDKg8afWM/s512/file-exists.png[/IMG]

I don't know how much of this has to do with my inexperience with Linux, and how much might have to do with outdated instructions. Synergy documentation (for all versions out there) is sadly lacking and most of it is at least a couple of years old.

Can *anyone* shed any light on this for me? Without Synergy running, Ubuntu is missing the last critical feature I need on it to be of any use to me.

Thanks.

BTW: I realize many forums discourage or don't allow bumping. I hope the mods will realize the only reason I'm bumping this is first, because it got no responses at first, and second, the entire contents of this OP is now changed.

Thanks again.

You appear to have lots of questions and really need to take them step by step to get a grip on what's going on.  Apparently you don't know how to use the vi editor.  So you could either explore the vi manual or use a different editor.  I find vi to be a bit confusing also.

I'll may, after 15 years take my advice and study the vi manual and practice using it since its such a common text editor and is referred to so many times.  I know just enough to make a simple change to some files... mainly after starting vi you can hit "i" to insert text and start typing and making changes.  You can also hit "o" to start typing.  Press ESC when you finish entering text and "Z" to close and exit the file.

I usually quickly install emacs and perform most of my console editing with it.  Gedit is a good gui editor that is usually installed by default in most OS'.  I'll suggest that you consider using gedit to edit your text files for now.

Try issuing:

```
gedit .synergy.conf
```to create/edit a .synergy.conf file in your home directory.

By the way which mode are you trying to run snyergy on your ubuntu machine, server or client?

As far as the changing text and bump, you might have considered posting a new update to your original post.  Using that method would not have warranted a bump nor an explanation for having to issue a bump.  ...just a thought.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-03
Thanks apollothethird. i'll have to take a closer look in a couple of days. A couple of comments though:

You're right, it does seem to be more than one question, which doesn't surprise me. After all, I do admit that although I may have quite a bit of experience with networking and Syngergy, when it comes to putting Linux/Ubuntu into the mix, I am a total noobie. And I don't mean to be the kind of noobie that simply won't "read the manual" first, however I am first trying to get a working environment up and running as quickly as I can so I don't have to bother anybody with too many noobie questions. It's quite difficult to put things in the manual to any practical use if the system isn't running the way it ought to first. This, along with one other occasional problem I've posted a different thread about, is pretty much the last thing left to get there and be able to be off and running more with the documentation and manuals rather than simply asking everything here.

That said, yes I could have left the original post as is, but the information that was in it is now obsolete, and would not be of much use to anyone trying to help me anymore, nor would it help anyone stumbling into this thread through Google, since so much of the set up was either wrong to begin with, and is now changed and basically irrelevant. Due to those reasons I felt it might be best for me, you, and everyone else looking for info on this problem if all the info here were as relevant to the current situation and distraction free as possible. ;)

BTW: The other problem I posted about might be related to why Quicksynergy won't work:

[http://ubuntuforums.org/showthread.php?t=1794427](http://ubuntuforums.org/showthread.php?t=1794427)

Maybe, maybe not...

---

### Post by apollothethird on 2011-07-03
> **Chris Richard said:**
> Thanks apollothethird. i'll have to take a closer look in a couple of days. A couple of comments though:

You're right, it does seem to be more than one question, which doesn't surprise me. After all, I do admit that although I may have quite a bit of experience with networking and Syngergy, when it comes to putting Linux/Ubuntu into the mix, I am a total noobie. And I don't mean to be the kind of noobie that simply won't "read the manual" first, however I am first trying to get a working environment up and running as quickly as I can so I don't have to bother anybody with too many noobie questions. It's quite difficult to put things in the manual to any practical use if the system isn't running the way it ought to first. This, along with one other occasional problem I've posted a different thread about, is pretty much the last thing left to get there and be able to be off and running more with the documentation and manuals rather than simply asking everything here.

That said, yes I could have left the original post as is, but the information that was in it is now obsolete, and would not be of much use to anyone trying to help me anymore, nor would it help anyone stumbling into this thread through Google, since so much of the set up was either wrong to begin with, and is now changed and basically irrelevant. Due to those reasons I felt it might be best for me, you, and everyone else looking for info on this problem if all the info here were as relevant to the current situation and distraction free as possible. ;)

BTW: The other problem I posted about might be related to why Quicksynergy won't work:

[http://ubuntuforums.org/showthread.php?t=1794427](http://ubuntuforums.org/showthread.php?t=1794427)

Maybe, maybe not...

It looks like you completely missed my point.  I brought up some components that might help you with Linux in general, but I did address your issue and asked you question pertaining to the issue.

You were having problems editing, and I gave you a command that should make your editing easy.  It might have been nice to know if, after using a workable editor, if you had better success.  Maybe yes, maybe no... of course if you continued to have problems, either I or someone else reading the thread could probably take you to a next step.

The question about the mode in which you wanted to add Ubuntu might help us to be able to assist you also.  I could probably give you a couple of liners based on the mode of Ubuntu (server or client in the mix).

You already gave a link that describes it all, so my describing it all again in a new message might not be exactly what you're looking for.  Picking first client or server might minimize some of the details of the description.

As far as changing changing a post, then writing a bump to ask the users to reread the previous post, that's one way.  Of course, you know more than I know since I didn't see the OP.  But there are times when seeing a development of change and progress can actually facilitate some understanding toward the ultimate objective.  I do it often.  I start out asking how to write a password script prompt for an html directory and end up learning that a better direction is learn how to configure and utilize features of the .htaccess file.

The whole thing is a learning experience and the other users gets to share in the social event.

But again, that was my response to your apology for having to be excused for the bump necessity.  Either way will work.  You don't have to consider it.  I just gave a response since you brought it up.

By the way, since you appear to be trying to add Ubuntu into the mix, it's probably the client, since in your OP you said you weren't having problems with any of the other machines, only Ubuntu.  So all you have to do is just run the synergy client module:

```
synergyc -n [client] [server]
```In the command above [client] is the name of the client machine (the name of the Ubuntu machine without the brackets) and [server] is the name of your Synergy server machine.  The one with the mouse and keyboard which is controlling the other computers in your network.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-04
> **apollothethird said:**
> It looks like you completely missed my point.  I brought up some components that might help you with Linux in general, but I did address your issue and asked you question pertaining to the issue.

Not at all. I got your point. I just wasn't able to address it just yet. Thus, "I'll have to take a closer look in a couple of days..." ;)

> **apollothethird said:**
>  were having problems editing, and I gave you a command that should make your editing easy.  It might have been nice to know if, after using a workable editor, if you had better success.  Maybe yes, maybe no... of course if you continued to have problems, either I or someone else reading the thread could probably take you to a next step.

Absolutely understood that. This is the part I will have to try later when I have a bit more time. Thank you very much for the suggestions.

> **apollothethird said:**
> The question about the mode in which you wanted to add Ubuntu might help us to be able to assist you also.  I could probably give you a couple of liners based on the mode of Ubuntu (server or client in the mix).

Actually I did explain this though I understand with the way I tend to explain things, it may have been easy to miss:

> 
Two clients running Windows XP SP3, and Synergy 1.3.1. 

**The Syngery server is a triple boot Mac Pro running OS X Snow Leopdard, Windows XP (new install, not yet completely updated, and Ubuntu 11.04.** Each OS is on a separate drive.


> **apollothethird said:**
> You already gave a link that describes it all, so my describing it all again in a new message might not be exactly what you're looking for.  Picking first client or server might minimize some of the details of the description.

True, but the explanations on that page wasn't working for me. Sometimes I need to hear the same thing from another person's mind perspective and wording. I am finding that more often than not the "how to's" posted on the web assume I already know many things I do not know.

> **apollothethird said:**
> As far as changing changing a post, then writing a bump to ask the users to reread the previous post, that's one way.  Of course, you know more than I know since I didn't see the OP.  But there are times when seeing a development of change and progress can actually facilitate some understanding toward the ultimate objective.  I do it often.  I start out asking how to write a password script prompt for an html directory and end up learning that a better direction is learn how to configure and utilize features of the .htaccess file.

I couldn't agree more, and normally I do leave the entire process there for all to see, but occasionally it isn't the best way. In this case the difference was that the synergy set up I had used a version I'm no longer using. I thought it was all working just fine on the other OS's, but in fact it was not. I had to change the Synergy versions entirely. Basically, what I had been doing had changed totally (because it didn't actually work at all), and since no one had responded anyway at that point.

A good analogy, I think, might be if I were investigating the best foundation type to use for a house, first asking for the best solution for deep clay soil, but while awaiting an answer and not having received one, I dug out all the clay and found bedrock. Now the entire situation and solution is different.


I do greatly appreciate your efforts. I didn't quote the remainder of your reply because, as you can see now, I am actually trying to use Ubuntu as the server, not the client.

A simple solution might be, I know, to switch to using one of the XP machines as client, however this machine is my primary box. I'm running OS X, Windows XP SP3, and Ubuntu all on separate drives using triple boot (Option key on startup because bootcamp and OS X can't "see" Ubuntu at all. Oddly, Bootchamp does though (this is a Mac Pro Intel by the way). The "optimal' solution is for this machine to be the server:

2 Windows XP SP3 clients

Mac Pro Intel:

OS X: Server
Windows XP SP 3: Server
Unbuntu: Server


Another reason for making this one the server is because although the Windows version allows for Synergy to start Synergys or Synergyc as a service (allowing me to switch screens and log into clients), Mac OS X versions won't run either server or client until I'm logged in (there is a way to do this, but the shared clipboard won't work if you do it this way). This means if the Mac is a client, every time I start up I have to have a separate keyboard hooked up to it in order to log in before Synergy will run. Setting up the Mac to run as server works best because it is the one machine I use the most, and even though I have to login to start the Synergy server, the keyboard is hooked up to it already anyway so it's not a problem, plus the shared clipboard works on the Mac OS.


I hope that makes sense.

I won't be able to try the editing options you suggested until tomorrow what with it being July 4'th and all (lot's of family stuff going on!), but if you happen to be able to respond in the meantime I do have one quick question.

In the third screen capture I posted. Using your suggestion, would I be opening that file for edit, or creating a new one?

I'm just wondering, if I have already created a config file somewhere, would it be better to delete that file before proceeding, and if so, how would I do that?

Thank you VERY much for your patience! :D

---

### Post by apollothethird on 2011-07-04
> **Chris Richard said:**
> I won't be able to try the editing options you suggested until tomorrow what with it being July 4'th and all (lot's of family stuff going on!), but if you happen to be able to respond in the meantime I do have one quick question.

In the third screen capture I posted. Using your suggestion, would I be opening that file for edit, or creating a new one?

I'm just wondering, if I have already created a config file somewhere, would it be better to delete that file before proceeding, and if so, how would I do that?

Thank you VERY much for your patience! :D


When you issue the command it'll create the file if it doesn't exist.  It'll open the file for editing if it does exist.

This is the behavior of most editors.

As far as making Ubuntu the service, that's fairly easy also.  One method is to use the QuickSynergy program and just fill out the names.  Change the names, “Above, Below, Right, Left” for host names of the other machines that are running the client.  If the clients are running you shouldn't have any problems.  It should work very seamless.

For the computers that are having problems finding the machine, you can use IP addresses instead of hostnames, but of course hostnames are easier at a glance.

You can also use the /etc/hosts file on Ubuntu to translate the IP addresses to the hostnames.  You can do the same thing on the Windows machine with the hosts file in “C:\Windows\System32\drivers\etc”.  I'm sure you can just as easy do the same thing with the Mac computer, but I haven't ever used a Mac.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-04
> **apollothethird said:**
> When you issue the command it'll create the file if it doesn't exist.  It'll open the file for editing if it does exist.

This is the behavior of most editors.

Can you explain, if you know, what the message means that I got in that last screen capture? That's what I got the second time (and get all the time now) when I try to create/edit the file.

It looks to me like it's saying the file already exists? 

It's the warning that I may end up with "two different instances of the same file" that concerns me...

> **apollothethird said:**
> As far as making Ubuntu the service, that's fairly easy also.  One method is to use the QuickSynergy program and just fill out the names.  Change the names, “Above, Below, Right, Left” for host names of the other machines that are running the client.  If the clients are running you shouldn't have any problems.  It should work very seamless.

That was my understanding, but for some reason Quicksynergy doesn't do anything at all.

> For the computers that are having problems finding the machine, you can use IP addresses instead of hostnames, but of course hostnames are easier at a glance.

This might work, but would mean I should set up static IP's for the clients. I actually tried setting up static IP's on both clients, in the 100's ranges so as not to interfere with other dynamic IP computers on the same LAN. Oddly, there were still some occasional conflicts, but I think I can overcome that problem. I do know that  setting up OS X with static caused Synergys to stop working altogether on that OS. No idea why. But I don't think leaving the server as dynamic should pose a problem.

I could be wrong....

It's been known to happen. :p

> **apollothethird said:**
> You can also use the /etc/hosts file on Ubuntu to translate the IP addresses to the hostnames.  You can do the same thing on the Windows machine with the hosts file in “C:\Windows\System32\drivers\etc”.  I'm sure you can just as easy do the same thing with the Mac computer, but I haven't ever used a Mac.


Good hint! If I can't get Quicksynergy to work, and straight IP's don't work either, I'll give this a try.

Shouldn't be necessary on Windows or OS X though, as I'm not having any problems with them anymore, but then I have seen some indications that one OS set up might mess with other OS settings (on the same computer that is), not just with Syngery, but with booting as well. I'm not totally certain that is what's happening though.

Thanks very much for the advice. I'll get back to this problem sometime tomorrow. 

Thanks again for your patience! :D

---

### Post by apollothethird on 2011-07-05
> **Chris Richard said:**
> Can you explain, if you know, what the message means that I got in that last screen capture? That's what I got the second time (and get all the time now) when I try to create/edit the file.

It looks to me like it's saying the file already exists? 

It's the warning that I may end up with "two different instances of the same file" that concerns me...

When you edited the file with which program?  I don't see a reference to your using gedit?

It's not possible to have two files by the same name in the same area, so that wouldn't be a problem.


> That was my understanding, but for some reason Quicksynergy doesn't do anything at all.Actually it give you a very quick layout.  It writes a quick configuration file and call the synergy server application with a link to that configuration file.  It's the same format that your original link gave you to create, and of course that I suggested that you use gedit for creating/editing.

By the way, I performed test and find that only hostnames in the server configuration works.  IP addresses don't work.

The client can poll the server with an alias and the server will respond by giving access to the keyboard and mouse.  So you don't need static IP addresses for the clients.  Just call the server and give the server your host hame.

This line from the client will work:

```
synergyc -n clientname servername
```The -n parameter is sending “clientname” as the client's hostname or alias.  Just configure the server to accept that alias and you're in business.  It's very simple with quicksynergy.  Just type the clientname in any of the fields.  Then just move the mouse toward that corner and beyond and you'd read that client.

Explaining it might sound complicated.  But it's really very simple.  Just type the client names in Quicksynergy and click execute.

If you decide to change configurations with Quicksynergy, you have to kill the synergys task that it would have started.  You can do that by typing:

```
killall quicksynergy
killall synergys
```I believe the whole operation is easier done than said.

> This might work, but would mean I should set up static IP's for the clients. I actually tried setting up static IP's on both clients, in the 100's ranges so as not to interfere with other dynamic IP computers on the same LAN. Oddly, there were still some occasional conflicts, but I think I can overcome that problem. I do know that setting up OS X with static caused Synergys to stop working altogether on that OS. No idea why. But I don't think leaving the server as dynamic should pose a problem.

I could be wrong....You don't need static IP addresses for the clients.  Just let the configuration file (or commandline) know who  the client is.  The server will use what the name the client sends it.



> It's been known to happen. 



Good hint! If I can't get Quicksynergy to work, and straight IP's don't work either, I'll give this a try.

Shouldn't be necessary on Windows or OS X though, as I'm not having any problems with them anymore, but then I have seen some indications that one OS set up might mess with other OS settings (on the same computer that is), not just with Syngery, but with booting as well. I'm not totally certain that is what's happening though.I can't imagine a scenario where one OS' configuration would have anything to do with another OS.  I believe you're mistaking to think it does.  Running a totally different OS is like running a totally different machine.  If your coworker plugged in his Laptop with his configuration, then left and you plugged in yours, they would operation totally independent.  That is the same as you changing OS' on your laptop.  The would work totally independent.

> Thanks very much for the advice. I'll get back to this problem sometime tomorrow. 

Thanks again for your patience! You're welcome... aways a pleasure.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-05
> **apollothethird said:**
> When you edited the file with which program?  I don't see a reference to your using gedit?

It's not possible to have two files by the same name in the same area, so that wouldn't be a problem.

Remember I have not yet tried your suggestion to use getit? That is the message I get when attempting to open with vi (according to the directions at [http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/](http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/)

I get that message even after closing all programs and rebooting.

I had to perform a bit of "memory refresh" in my own head on this, but now I'm pretty sure what the message means, and  that it really doesn't matter at this point.

My understanding of the ".swp" file is that is a "temp" file created while editing a text file. That should be automatically deleted once the program editing the file is closed. Correct me if I'm wrong. 

I wasn't implying it was possible to create two files with the same name. I am well aware that is not possible. It is possible though, to have a "temp" file (in this case apparently with ".swp" extension) "hanging" hidden in a folder, indicating to all editors (if everything is working properly), that the file is already being edited by another process. In this case, that clearly isn't the case, because there are no editors open and I've even rebooted numerous times since first attempting to edit the file. 

I believe the ".swp" file is still there simply because I quite the terminal while I had it open, thus never giving vi the chance to save it and delete the swap file on its own. :?:

I guess it doesn't really matter then whether it's opened by any editor and saved again.

On a side note: I just went into the etc folder and viewed hidden files. There are actually four of them (.syngergy.conf.swm, .swn, .swo, and .swp), which indicates to me every time I try to edit the file (which hasn't actually been created yet as "synergy.conf, yet), I'm creating yet another copy of the file with a different extension. But that is another discussion...


> Actually it give you a very quick layout.  It writes a quick configuration file and call the synergy server application with a link to that configuration file.  It's the same format that your original link gave you to create, and of course that I suggested that you use gedit for creating/editing.

Yes, I understood this is what Quicksynergy is *supposed* to do, but it isn't doing anything at all for me. No configuration file is being created at all. No connections are being made by Quicksynergy.

> By the way, I performed test and find that only hostnames in the server configuration works.  IP addresses don't work.

Really?! IP's are, from what I recall, supposed to work if they are used in the configuration file. I know in the Windows version I'm "supposed" to be able to use IP's.  

> The client can poll the server with an alias and the server will respond by giving access to the keyboard and mouse.  So you don't need static IP addresses for the clients.  Just call the server and give the server your host hame.

Theoretically, yes. But if IP's were able to be used (which you just indicated doesn't work), they would have to be static, otherwise with DHCP the IP's would eventually change, and syngery would be unable to connect to the correct computers.

Incidentally, did you try IP's in Quicksynergy only? (In the GUI interface or right in the configuration file?), or without it?

> This line from the client will work:

```
synergyc -n clientname servername
```The -n parameter is sending “clientname” as the client's hostname or alias.  Just configure the server to accept that alias and you're in business.  It's very simple with quicksynergy.  Just type the clientname in any of the fields.  Then just move the mouse toward that corner and beyond and you'd read that client.

Explaining it might sound complicated.  But it's really very simple.  Just type the client names in Quicksynergy and click execute.

This is what I have been trying to explain, but I guess it's not coming through clearly. I've already tried Quicksynergy, several times. NOTHING happens. I cannot even find a configuration file anywhere in the system after performing operations in the QS GUI interface. (EDIT: My apologies! I did finally find the config file for QS, but Synergy still isn't functioning yet.)

For whatever reason, on this particular system, it isn't that simple.

> I can't imagine a scenario where one OS' configuration would have anything to do with another OS.  I believe you're mistaking to think it does.  Running a totally different OS is like running a totally different machine.  If your coworker plugged in his Laptop with his configuration, then left and you plugged in yours, they would operation totally independent.  That is the same as you changing OS' on your laptop.  The would work totally independent.

I may have misspoken on this point just a bit. What I actually was [mostly] referring to was Synergy set up on one OS, which may require changing settings/Synergy versions on the clients, can, and does cause some problems. I found I must keep very close track of what  works on one OS, but doesn't on another.

There have most definitely been some booting conflicts as well, that I'm almost positive are caused by OS X boot process becoming "confused" (for lack of a better term), due to the way things are set up on this system. I do know that if I start playing around too much with various ways of booting into different systems, eventually I'll start getting errors booting up Windows. But that too is another discussion. As long as I only use the option key during boot-ups and reboots, there doesn't seem to be a problem. Using Bootcamp or "Bootchamp" seems to start causing problems.

BTW: I actually have used the pico and vi editors in the past, but it's been a few years and I did drop out of the class so it's not all very fresh in mind right now. Time to dig up the book I guess! :)

Thanks again!

---

### Post by Chris Richard on 2011-07-05
Okay, some progress. At least I know what is and isn't working now.

Synergy processes are working. I can see either quicksyngery and/or synergys running in processes depending on which I've started. Configuration files for either/both are where they should be, and set up correctly. (I have actually set up manual configurations  files numerous times on Windows, so I do know how to read them just in case you're wondering ;))

Connection however, is not happening.

Now I'm pretty much back to suspecting the versions in Ubuntu aren't compatible with the client versions (1.3.1). Unfortunately, determining Syngergy versions without the GUI interface, I have found, can be a challenge.

Any idea which version is being used in Ubuntu?

I realize I'm running an older version on Windows, and wish I could remember at this moment why. There is a reason for it but I can't remember the specifics. All I can say right now is that using newer versions presented problems on one  OS or another.

---

### Post by Chris Richard on 2011-07-05
It sure would be nice if at least SOME instructions that I've found posted on the web would include a list of assumptions. Such as:

"These instructions assume you have Samba installed."

Well. I do now, and Syngergy finally works as it should.

That seems like a very odd thing not to include in the core OS.

No matter. Finally, after almost three weeks, I have a fully functional Ubuntu environment with virutally everything working just as I need it to. :p

Now I'm off to find out whether I can move the Launch bar, which, on the left, I can no longer open if windows are maximized, since that leads to my print server. Need to find out why Google Chrome keeps crashing too, but those are for other posts if I even need to bother at all. I bet the info is  already out there somewhere...

@apollothethird: Thanks a bunch for your undying patience. Works a whole lot better when Ubuntu is actually connected to the LAN. ;)

---

### Post by apollothethird on 2011-07-05
> **Chris Richard said:**
> It sure would be nice if at least SOME instructions that I've found posted on the web would include a list of assumptions. Such as:

"These instructions assume you have Samba installed."

Well. I do now, and Syngergy finally works as it should.

That seems like a very odd thing not to include in the core OS.

No matter. Finally, after almost three weeks, I have a fully functional Ubuntu environment with virutally everything working just as I need it to. :p

Now I'm off to find out whether I can move the Launch bar, which, on the left, I can no longer open if windows are maximized, since that leads to my print server. Need to find out why Google Chrome keeps crashing too, but those are for other posts if I even need to bother at all. I bet the info is  already out there somewhere...

@apollothethird: Thanks a bunch for your undying patience. Works a whole lot better when Ubuntu is actually connected to the LAN. ;)

Hi, Chris.  Thanks for the expressions of appreciation.  I'm very glad to help.  I have received a lot from various generous users of the Internet and try hard to do my part in giving back.  An expression of appreciation is always a nice dividend.

I see you also placed an effort to give back by attempting to mark the thread as solved.  This is a great feature of many forums that facilitate users having similar problems.  They can give priority to the topics flagged as solved and have confidence they might find their relief in one of those topics.

To really mark the topic as solved use the Forum Tool link at the top of the page.  When the gurus see this, it inspires them to work harder with the users they see giving back.

Glad for your success.  I became more efficient with synergy by testing examples that I was trying to explain to you.  That's another fringe benefit I get from working hard on giving back.

By the way, a samba install isn't a prerequisite for Ubuntu to work properly.  All the client has to do is send the name by which they want to be referred.  The server will already have the IP of who is talking to it.  It just needs a name to associate with who it's going to give access to and at which location.

Have a good one!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-05
> **apollothethird said:**
> To really mark the topic as solved use the Forum Tool link at the top of the page.  When the gurus see this, it inspires them to work harder with the users they see giving back.

Yeah, I see it now. Was wondering where it was, did a search and found some older thread that said it wasn't there anymore, so I never looked any further, assuming it was still gone. Couldn't see it, of course, because the loaded thread was not mine. The obvious often flies right over my head.


> By the way, a samba install isn't a prerequisite for Ubuntu to work properly.  All the client has to do is send the name by which they want to be referred.  The server will already have the IP of who is talking to it.  It just needs a name to associate with who it's going to give access to and at which location.

And this comes as not much of a surprise to me. I'm sure you will agree though, that networking issues and solutions, out of the box, are nothing whatever like Windows or Mac OS out of the box. 

What I do know is Samba worked. I didn't search it out and intentionally use it though. I stumbled on it while trying to access network folders. Got a message that "the appropriate software was not yet installed," so went to see what would happen if I tried to turn on file sharing, and that's when Ubuntu offered to install it. 

The thing is, not that I want to stretch this thread into an entirely different discussion, it's extremely difficult to learn any OS if the OS isn't up and running at full potential within the systems among which it will be used. I really think for the most part Linux noobies first want a running and fully functional OS, and then should be willing to begin really digging in and learning about it. If it isn't fully functioning, depending on the rest of the system's environmental variables, that could be next to, if not entirely impossible.

Thankfully (I think...), I knew before I got into this getting to that point was likely to be a long haul. I already knew that precisely *because*  Linux is designed to work on almost any configuration out there, there is no possible way to write a truly effective "Dummies" book that will work on so many different systems.

I did almost give up a few times. And of course, every time I think "this is the last thing I need to fix" there comes yet another...

Damn! No M-Audio drivers! ](*,):roll:

:lol::lol::lol::lol::lol:

---

### Post by apollothethird on 2011-07-05
> **Chris Richard said:**
> Yeah, I see it now. Was wondering where it was, did a search and found some older thread that said it wasn't there anymore, so I never looked any further, assuming it was still gone. Couldn't see it, of course, because the loaded thread was not mine. The obvious often flies right over my head.




And this comes as not much of a surprise to me. I'm sure you will agree though, that networking issues and solutions, out of the box, are nothing whatever like Windows or Mac OS out of the box. 

What I do know is Samba worked. I didn't search it out and intentionally use it though. I stumbled on it while trying to access network folders. Got a message that "the appropriate software was not yet installed," so went to see what would happen if I tried to turn on file sharing, and that's when Ubuntu offered to install it. 

The thing is, not that I want to stretch this thread into an entirely different discussion, it's extremely difficult to learn any OS if the OS isn't up and running at full potential within the systems among which it will be used. I really think for the most part Linux noobies first want a running and fully functional OS, and then should be willing to begin really digging in and learning about it. If it isn't fully functioning, depending on the rest of the system's environmental variables, that could be next to, if not entirely impossible.

Thankfully (I think...), I knew before I got into this getting to that point was likely to be a long haul. I already knew that precisely *because*  Linux is designed to work on almost any configuration out there, there is no possible way to write a truly effective "Dummies" book that will work on so many different systems.

I did almost give up a few times. And of course, every time I think "this is the last thing I need to fix" there comes yet another...

Damn! No M-Audio drivers! ](*,):roll:

:lol::lol::lol::lol::lol:

I understand the general consensus by many that there's something hard about Linux, but I don't agree with it.  I've been giving computer support for a very long time.  Longer than anyone I  know.  I started back in the early 80's.  I find it much easier to support Linux.  I find it easier.

I used to setup and install Windows on many of my client's new computers, but that was mainly because of the popularity and compatibility with their friends.  It was never because I thought it was easier.

Linux (and Unix) has always been easier and more stable for me, even back in the days when the environment I was using was console based Unix and console based Microsoft (DOS).

I have recently started installing Linux on the computers of new computer users.  It's much easier to support.  It's very similar to most people who start out with Mac's and use Mac's all their life.  They feel a bit crippled when forced to use Windows for a few sessions.  This also goes vice-versa for many Windows users who are forced to use Mac's for a few sessions.  Linux is the same.

If someone had gone all their life using only Linux and all their friends, peers, business and school associates were using Linux and they were forced to use a Windows or Mac OS for a session, they would feel very crippled.

I started out my serious computer environment with a Tandy Color computer running OS9 (a Unix type OS).  Development on the Color computer stopped and I went to a Microsoft computer.  I always found it very limited in nature, but used it because it was the most popular and easiest to access.  After a few years I purchased Unix OS (Sco Unix) which cost almost $10,000 at the time.  I used it for all my serious work until the late 90's.  I used Windows a lot, for the ability to support what my customers were using.

I'm glad to see that more and more the most stable, reliable, and powerful OS is gaining in popularity.  There is a good chance you might start realizing this.  I believe the sooner might be the better.

I understand how hard it is for a new Linux user to see this.  It's almost impossible.  A person will naturally, for a long time, try to use the new environment like the old environment and look at the differences as flaws.

I'm not trying to convert your thinking and make you put Linux above the other OS'.  I'm just sharing with you some of what you might learn.  Having this vision as a possibility might make the road a little easier to travel.

By the way, I found the Linux synergy configuration much easier than the Windows configuration.  Much of the operation of Windows programs are hidden from the user.  The configuration files are scattered all over the place and gets worse and harder to handle in each version of Windows.  I never spent much time with the Mac, but I found most of what I wanted to do a nightmare if I for some reason had problems.  I understand it had a lot to do with my not being a Mac user.  But there were times when I tried to give support to Mac users and found I had to reboot for just about everything I worked on to take effect.  I'm thinking particularly back in 90's when I used to setup dialup connections for Mac users.

People have problems with all their OS'.  There's always a market for computer support people.  Because of the ease of operation and stability of Linux, I find it much easier to support.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Chris Richard on 2011-07-06
I'm beginning to wonder if we might want to ask the mods to split this into its own thread. :)

I actually come from a background that began with Macs, migrated to Windows for many years, then went back to Mac.

THE main reason I have been wanting to use Linux has nothing to do with frustration over either OS. It's just that I'm one of only a few people I know personally that has spent so much time on both systems.

I am NOT by any means adept enough at any system to, say, open up a shop, but I am, in comparison to most users, a "power user." (Which from my perspective just means I'm not afraid to break things by experimenting. :P) I'm daring enough to try almost anything, and stubborn enough to make it work by whatever means necessary within the bounds of knowledge I possess along with as little "new" knowledge as necessary to get what I want.

Before I even started looking seriously at Linux, I had already learned the clear differences between Windows and Mac in terms of actual usage, reliability, and philosophies of both users and developers. By the time I decided to dive into experimenting with Linux I already knew that both the developers and users (especially long time users like yourself), were coming from a totally different mind-set. I was prepared for stumbling blocks, surprises, and at least some frustration. 

Most of the frustration new users experience, especially in recent years, is definitely coming from dealing for years with either Mac or Windows, and expecting Linux to work in preconceived ways. I think of it as similar to driving a car for decades, then suddenly jumping into a helicopter and looking for the steering wheel. :shock:

All three are different animals, built with different ideas of what users ought to be able to do and how they ought to be able to do it. When things don't work as users "expect them to," these days at least there are a lot more users who are likely to say there are bugs, or the system is just plain "broken." I know that's not necessarily the case. Just because a car built in Britain has a steering wheel on the right doesn't mean it's broken or flawed. It just means the steering wheel isn't where I'm used to seeing it.

Linux, for straight "users" with little to no training in computer principles, is most definitely very difficult. The more one understands about what goes on "under the hood," the easier it is. I am, I think, about halfway between the two groups, with a slight bias toward the more "tech-minded" group.

> By the way, I found the Linux synergy configuration much easier than the Windows configuration.

Once I realized the real problem here was simply the fact that the Linux OS was not even connected to mt LAN, I also realized that the configuration process was almost identical, except for the "Quicksynergy factor," which meshes nicely with your next point. 

> Much of the operation of Windows programs are hidden from the user.

I'm not sure I agree with this entirely. Not if what you mean is "in comparison to Linux." Of course, the only honest comparison I can make right now is to the Ubuntu package. I'm sure to you it seems this way, but then you have nearly thirty years of experience with Linux. I think you'll have to admit that a lot of  what seems transparent to you, wouldn't to the average Windows or Mac user.

The interesting thing to me is this. I have always known that "windows" (be they Mac or Windows) are just an illusion. A representation of what really goes on, on the HD and in RAM. How many people are really left on this  earth that could look at a bank of binary lights and read them? How many people can even write anything in machine language anymore?

Even the command line is an illusion. There are few who can mentally envision what's actually happening when commands are executed, and even most of them, I dare say, probably tend to visualize it in some form, and probably more often than not, as some sort of physical file system. Most users never think twice about it. Most never ask questions like "Where are these files, *really*?" They simply assume they are where they see them in the GUI. Even many who do ask that question either don't know, or never think about the fact that once they do think they know were all the files really are, they are wrong yet again.

Command line or not, every OS is just a representation of something no human eye will ever see.

Command line though, DOES require a more in-depth of understanding beyond the multi-layered illusion of folders and windows (why aren't the windows "drawers and cabinets" anyway? ~ I've always wondered that :-k)

And that brings me to these new GUI Linux interfaces, that are clearly aimed at users who are more used to GUI. Frankly, I find it far easier with Windows in particular, to "see" what goes on under the hood, and even change quite a bit of it.

I'm certain one can do much more with Linux in this respect, but it's pretty darned clear already it ain't gonna be done with a GUI. Not for a while anyway.

It all comes down to what people are accustomed to. Many who've been using terminals to do most of their work are frustrated with the move toward GUI. Many who are long time GUI users are frustrated with the amount of terminal usage required to get things done. It's not a stretch of logic to claim that the latter is a much larger group, and quickly becoming far larger than ever before. Linux developers obviously recognize and accept this reality, otherwise they wouldn't be moving so fast in the direction of GUI. Linux GUI though, clearly has quite a ways to go before it's anywhere near as easy to use, and as powerful as Mac or Windows. 

But I do see that day coming. And I think it's coming much faster than most of us believe it is, and much faster than a lot of Linux veterans would probably like. I think we're seeing the tip of the iceberg. And iceberg that will hopefully include the best of both worlds. I love the ability to simply point and click to make things happen. It's so much  more efficient than writing complex program lines. But I also love having the choice to get under the hood and change whatever I want. I don't see that happening in the Mac or Windows world, EVER. Not to the extent  that Linux already allows, and probably always will.

EDIT: You know everything I have to say right now regarding Linux really needs to be taken with huge helpings of salt. After all, I just barely got a running OS only yesterday, so I really haven't had much of an opportunity yet to really dig deeply. That's going to take some time obviously. And now that I actually do have a stable install, working in every way I need it to, I will now be able to do it. All I have to do now is find the time.

---


---
title: "ndiswrapper admin password"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by dtconnor on 2013-05-02
I installed ndiswrapper but I can not open it because it does not except my admin password.
Since Ubuntu disables root and requires sudo what would be my root pw?
I only have one user, me, with admin priv and that password does not work. 

Older videos show going into system>system admin but the are older versions of Ubuntu
so that does not work in the case of Ubuntu 13.04

---

### Post by mörgæs on 2013-05-02
Are you sure that you actually need ndiswrapper and there's no other solution? 
Which netcard do you use?

---

### Post by dtconnor on 2013-05-02
No I don't actually need it for this laptop &#8211; wireless is working - I just switched from Windows after years and years andI am trying to learn all I can.
This will not be the last PC that I convert and I am just curious about this stuff like ndiswrapper and adzapper etc.
I just keep reading this forum and want to try everything out - I know curiosity killed the cat but I can pretty much &#8211; usually &#8211; figure almost anything out in Windows so I want to be as proficient in Linux.
 

 I read that Ubuntu disables root and uses sudo &#8211; I read enough to get the concept &#8211; so obviuosly I do not have a root pw just my user which has admin priv password. Sooooo what is the root pw ??????
 Obviously the root password issue must come up for other stuff in Ubuntu so how is it handled?

---

### Post by Cheesemill on 2013-05-02
There isn't a root password. You just use sudo along with your own password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dtconnor on 2013-05-02
OK - then why when ndiswrapper asks for the admin pw my user pw does not work - btw there is only one account on this system - mine  and is Admin user.

---

### Post by oldrocker99 on 2013-05-02
Hmmm...in ChrUbuntu, the default user is "user" and the password for that account is user. Try that; your system might be similar.

---

### Post by Cheesemill on 2013-05-02
> **dtconnor said:**
> OK - then why when ndiswrapper asks for the admin pw my user pw does not work 

Can you give us more details please, what exact command were you trying to run and what was the output (you can copy and paste from the terminal into your post).

---

### Post by dtconnor on 2013-05-02
I loaded ndiswrapper from Synaptic
then clicked on the icon 
a window pops up asking for the Adminstrative password
I put my password in the password box
tells me incorrect password

For some reason I cannot print screen when the dialog box is up

---

### Post by Cheesemill on 2013-05-02
Do you know what you installed to give you an ndiswrapper icon to click?

Ndiswrapper is a command line program that you run from the terminal, it doesn't usually have an icon that you click on unless you install something else as well.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by dtconnor on 2013-05-02
Well I am a noob so I may be confused but I definitely did not install this from the command line. And I definitely installed ndiswrapper from Synaptic. The icon is to monitors with wrench and a screwdriver. When I go into Dash and begin a search ndi the icon pops up. It is labeled Windows Wireless Drivers

---

### Post by snowpine on 2013-05-02
Try:

```
sudo ndiswrapper
```

and use your user password. (User must be in the sudo group as described [here]("https://help.ubuntu.com/community/RootSudo").)

---

### Post by dtconnor on 2013-05-02
I get a list of I guess what you might call syntax for command arguments
The videos show how to download Windows drivers and then use graphical interface to add it to the kernel.
This sounds like a great tool - since I spen a lot of time getting my broadcom NIC up and running in 12.10
I would really like to know how to use this tool in the future - but the app wants a password and I have no idea what password it thinks it wants.

---

### Post by snowpine on 2013-05-02
You should **read** the command syntax, because it will explain how to use ndiswrapper.
The password as I mentioned is your sudo user's password; did you get an error message to indicate this is not the case?

I think you are thinking of **ndisgtk** which is a graphical front end for ndiswrapper. You can run it with:

```
gksu ndisgtk
```

**HOWEVER** I agree wholeheartedly with mörgæs's advice in post #2: ndiswrapper is more or less deprecated and you should follow this tutorial for your Broadcom card: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Broadcom has **excellent** support in Linux through the native driver. :)

---

### Post by dtconnor on 2013-05-02
OK - this starting to make more sense
I recognize ndisgtk
I have no problem with sudo - my password works
And now I see the command syntax

BTW when I eecute gksu ndisgtk I get the dialog box I have been talking about
and of coures it wants a password - and whatever that password is it is not my sudo password.

My broadcom NIC is not an issue as we speak I went through that pain with 12.10

---

### Post by snowpine on 2013-05-02
There is some information here that may or may not be relevant: [http://askubuntu.com/questions/48215/password-not-working-in-graphical-applications-gksu-works-with-sudo](http://askubuntu.com/questions/48215/password-not-working-in-graphical-applications-gksu-works-with-sudo)

Apologies I cannot be of further assistance but I don't use ndiswrapper, personally.

---

### Post by dtconnor on 2013-05-03
IT WORKS ! THX!

Well you may not use ndiswrapper but you sure figured out where to get the answer.
I just think this will be a useful tool to know.

You guys are awesome - I get all kinds of crazy info all over the internet 
that usually does not work btw - but the advice I get here is always spot on.    

basically this is the explanation;
"[COLOR=#444444][FONT=Ubuntu Beta] gksu is a frontend to both sudo and su, and when a sudo-using OS like Ubuntu has working 
gksudo and broken gksu, it is almost always because the authentication mode is incorrectly set to su"[/FONT][/COLOR]

---

### Post by mörgæs on 2013-05-03
Good that you like it here.
Soon you will be the one helping people :-)

Please mark the thread 'solved' like this:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dtconnor on 2013-05-03
there was no prefix box so I edited the title
-break-
I tried Ububtu 12.10 based on a recommendation (actually 12.04 was the recommendation)
then I researched RAID  as I am running RAID 0 on a high end desktop with Windows 8
turns out 13.04 may be my answer - not sure yet - but I wanted to play with it so I upgraded
12.10 on my laptop to 13.04
The upgrade did not go well but an Install off the DVD fixed everything - and all is fine now.

---


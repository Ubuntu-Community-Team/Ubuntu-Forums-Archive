---
title: "Still no Windows File Sharing out of the Box"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by windyweather on 2010-01-22
Back in Gutsy days I did some work to make Windows File sharing work. [Here's the post I did then]("http://www.windyweather.net/wp/2008/02/23/ubuntu-samba/").

Now I've upgraded one machine to 9.10 and installed another one from scratch. They are all fully updated to the latest. I was surprised by several things.

[LIST=1]
[*]Windows file sharing still does not work with 9.10 out of the box. If we don't want to bundle it, then at least we could make a single package - WindFileShare, which has all the dependencies so that it's dirt simple to make it work. We can do that, right? Make a fake package that only has dependencies for WinBind, Samba, SMB, SMBCLient, etc etc. so that it drags all the parts in and configures them? Isn't windows file sharing important enough to do that??

[*]The process of getting things working was still the same. Randomly install a few things, Change a couple of config files etc. Not a pretty sight for the casual user with a new Linux netbook.

[*]And when it's all done, there is still something wrong with it. Vista cannot look into the Karmic system, but the Karmic system can look into Vista with no problem. Works fine both ways with WinXP.

[*]The [documentation for setting it up is very confusing]("https://help.ubuntu.com/community/SettingUpSamba"). And has not been changed to reflect anything new. Still doens't enable Winbind either, which is necessary if you want to check the network with ping.
[/LIST]

Here is my [Previous Post for Gutsy]("http://www.windyweather.net/wp/2008/02/23/ubuntu-samba/").
[Here is my new Post for Karmic]("http://www.windyweather.net/wp/2010/01/22/ubuntu-karmic-koala-windows-file-sharing/").

Sure seems that windows files sharing is interesting if we are going to make Ubuntu friendly to use with the world that's out there.

Thanks for listening,
- windy

---

### Post by stinger30au on 2010-01-22
with 9.10 you can either do a
sudo apt-get install samba

or 

create a directory on your desktop (folder) and right click and click on share and share the folder and follow the prompts and it will auto magically add samba and whatever else it needs and will tell you to restart once done

---

### Post by windyweather on 2010-01-22
> **stinger30au said:**
> with 9.10 you can either do a
sudo apt-get install samba

or 

create a directory on your desktop (folder) and right click and click on share and share the folder and follow the prompts and it will auto magically add samba and whatever else it needs and will tell you to restart once done

Actually that was the first thing I did on the new install and it failed. What I actually did was to open a local file browser, right click on my home directory, darrell, and then open the Sharing Options dialog.

Here's the screenshot. After that failed, I dropped back to doing the same install as the upgrades system, WHICH DOES WORK, and the new install does not work, as I said in detail in my blog posts.

Maybe we can figure out what went wrong.

- windy

---

### Post by Morbius1 on 2010-01-22
Here's the thing: I does work out of the box ( if I add the samba package )- at least for me.

My network consists of , at any given time, a mix of WinXP, linux, and Macs. These are all basic installs and I can share resources between all of them. These are some of the things I have NOT done to accomplish that:

I have not installed or configured Winbind.
None of my workgroup names match.
No editing of nsswitch.conf
Never changed the resolve order
security = user as it should be

There's nothing special about my network hardware:
DSL Modem > Ageing DLink 604 Router + Wireless Access Point.

There is a Vista laptop that comes by every now and then and I did notice some peculiarities and I don't remember now what I did to resolve it, but I'm guessing that for most folks it does work.

There are enough posts on every linux forum to prove your point that something fundamental is missing from the base configuration  that needs to be changed so that my experience is universal. I'm just not sure what that is.

---

### Post by windyweather on 2010-01-22
Just to summarize the situation.

[LIST=1]
[*]Sharing with Ubuntu as the client works for both the upgrade and the fresh install.
[*]Sharing with XP as the client works to both Ubuntu servers.
[*]Sharing with Vista x86 and x64 as the clients both fail with the new install as the client, but works fine with the upgrade install.
[*]On the new install, doing the Share Options thing above works for a sub-folder of darrell, but does not change the failure to connect from Vista[s].
[/LIST]

- windy

---

### Post by Morbius1 on 2010-01-22
Why not post the output of the following commands from the machine that Vista cannot access:
[B]
net usershare info[/B]
**testparm -s**

---

### Post by capscrew on 2010-01-22
> **Morbius1 said:**
> Here's the thing: I does work out of the box ( if I add the samba package )- at least for me.

My network consists of , at any given time, a mix of WinXP, linux, and Macs. These are all basic installs and I can share resources between all of them. These are some of the things I have NOT done to accomplish that:

I have not installed or configured Winbind.
None of my workgroup names match.
No editing of nsswitch.conf
Never changed the resolve order
security = user as it should be

There's nothing special about my network hardware:
DSL Modem > Ageing DLink 604 Router + Wireless Access Point.

There is a Vista laptop that comes by every now and then and I did notice some peculiarities and I don't remember now what I did to resolve it, but I'm guessing that for most folks it does work.

There are enough posts on every linux forum to prove your point that something fundamental is missing from the base configuration  that needs to be changed so that my experience is universal. I'm just not sure what that is.

I feel I must add my experience with SMB (both Windows and Samba) to the conversation.  At the present time I have a 2 Ubuntu Samba server, heterogeneous client(s) (XP, Vista, Win7 and Ubuntu Desktop) network.  My installations have no WINS or NetBios naming at all!  Windows has not needed NetBIOS since Win2K.  The reliance on NetBIOS is a convenience not an absolute.  DNS is the better way to perform name services.

For definitive explanation of SMB (CIFS) and how it works, see [**_[COLOR="Navy"]here [/COLOR]_**]("http://ubiqx.org/cifs/SMB.html").

Winbind is definitely **not **essential to a completely functional Samba installation. Winbind is for joining Samba to a Windows AD Domain. I don't believe it really has anything to do with the install except to get the system to not squawk when the nsswitch.conf file is configured.  The nsswitch file itself is not needed as long as the LAN has DNS configured correctly.

The specific problem the OP has with Vista authentication is due to the use of NTLMv2 on MS Vista and Win7.  If this is turned off in the VISTA and Win7 clients or accommodated in the Samba install those clients will work just fine.

In short; NetBIOS is not mandatory, but some nameservice must be in place.  NTLMv2 must be dealt with.  Either by turning it off or configuring Samba to accommodate it.

---

### Post by capscrew on 2010-01-22
> **windyweather said:**
> Just to summarize the situation.

[LIST=1]
[*]Sharing with Ubuntu as the client works for both the upgrade and the fresh install.
[*]Sharing with XP as the client works to both Ubuntu servers.
[*]Sharing with Vista x86 and x64 as the clients both fail with the new install as the client, but works fine with the upgrade install.
[*]On the new install, doing the Share Options thing above works for a sub-folder of darrell, but does not change the failure to connect from Vista[s].
[/LIST]

- windy
I feel the issue is NTLMv2 authentication used on Vista and later MS products.  See [**_[COLOR="Navy"]here [/COLOR]_**]("http://blog.crankybit.com/vista-samba-ntlmv2/")for more information.

---

### Post by Morbius1 on 2010-01-23
> **capscrew said:**
> The specific problem the OP has with Vista authentication is due to the use of NTLMv2 on MS Vista and Win7.  If this is turned off in the VISTA and Win7 clients or accommodated in the Samba install those clients will work just fine.... NTLMv2 must be dealt with.  Either by turning it off or configuring Samba to accommodate it.

First off, I'm not sure from the tone of your post whether you are agreeing with me or not :). Since nothing you wrote disagrees with anything I wrote I'm going to assume the former. 

Here's the problem with NTLMv2 as I understand it:

As a linux client to a Windows Vista or Win7 server ntlmv2 is not enabled by default. One must add '**client ntlmv2 auth = yes**' to smb.conf on the client to access the Windows share.

As a Samba Server however, ***it's my understanding*** ( and trust me I'm no expert ) that ntlmv2 is implemented by default.

windyweather's problem is accessing the Samba Server form a Vista client. I think there is something else missing.

---

### Post by capscrew on 2010-01-23
> **Morbius1 said:**
> First off, I'm not sure from the tone of your post whether you are agreeing with me or not :). Since nothing you wrote disagrees with anything I wrote I'm going to assume the former. 


I was in agreement. :D  I wanted to add support to your observations.
> 

Here's the problem with NTLMv2 as I understand it:

As a linux client to a Windows Vista or Win7 server ntlmv2 is not enabled by default. One must add '**client ntlmv2 auth = yes**' to smb.conf on the client to access the Windows share.


This does not seem to be true in all cases.  I have Linux clients (Ubuntu Hardy).  They do **_not_** have '**client ntlmv2 auth = yes**' in the smb.conf file.  They interact with my Vista shares correctly.

I think we have a moving target here.  My guess is that MS has backed off the  NTLMv2 authentication.  My Vista clients show that it is now **not ** turned on by default.  I'll bet NTLMv2 was suppressed with a service pack. 
> 

As a Samba Server however, ***it's my understanding*** ( and trust me I'm no expert ) that ntlmv2 is implemented by default.
I believe this was after 3.0.22.

**Just a guess here:** As NTLMv2 is not new (used in Win95/98 ) the *implementation *has always been there.  The default was changed to *yes* rather than no.

---

### Post by windyweather on 2010-01-23
So.... The bottom line I'm hearing is that we still don't have a clue?

Recall that I'm using identical SMB.CONF files on both systems.
That Vista will connect to the upgraded system.
Vista will not connect to the freshly installed system.
Both systems will operate just fine as client to a VISTA server.
and that WINBIND is now active on both systems. [irrelevant to security]

So, we think that there is something besides SAMBA config to check.

Can anyone suggest where else to look for differences??

Thanks,
- Windy

---

### Post by windyweather on 2010-01-23
I forgot a step that I documented in the previous post on my blog.
To use samba setting security = user you must:
> 
Update: Here’s the fix for security = user to work.

You need to add a password to the separate Samba password database. Use the following for each user and change security = share to security = user.

darrell@squall-ubuntu:/etc/samba$ sudo smbpasswd -a darrell
[sudo] password for darrell:
New SMB password:
Retype new SMB password:
darrell@squall-ubuntu:/etc/samba$

I missed this until just now.
Sorry for all the confusion.

But... this makes the point that for Ubuntu to work out of the box is not a trivial process. 

Not only must you add WINBIND, and SAMBA [which may be configured auto magically if you like], but you need to do some terminal magic to set a SMB password or VISTA will not connect. 

Right?? Ubuntu 9.10 is not ready to play with windows OOTB.

 - windy

---

### Post by capscrew on 2010-01-23
> **windyweather said:**
> I forgot a step that I documented in the previous post on my blog.
To use samba setting security = user you must:


I missed this until just now.
Sorry for all the confusion.


So I guess we can chalk this up to operator error?  :oops:
> 

But... this makes the point that for Ubuntu to work out of the box is not a trivial process.

Where is the claim that setting up Samba (in the conventional way) is **supposed to be **trivial. >  

Not only must you add WINBIND, and SAMBA [which may be configured auto magically if you like], but you need to do some terminal magic to set a SMB password or VISTA will not connect. 

You may need to setup WINBIND to get Samba to work.  Samba itself does not require it.  One has always needed the *smbpasswd * to function correctly using conventional configuration.> 

Right?? Ubuntu 9.10 is not ready to play with windows OOTB.

 - windy

Maybe, maybe not.  Certainly not if you are going to use the classic method of configuration.  But who said it was "*ready to play with windows OOTB. *"

It would be interesting to try and configure complete system (2 way communication) with a Ubuntu and Vista hosts using Nautilus.  This would mean that we are relying on Gnome's GVFS developers to properly implement the Samba configuration.

---

### Post by Morbius1 on 2010-01-23
> To use samba setting security = user you must:
[QUOTE]Quote:
                                                 Update: Here&#8217;s the fix for security = user to work.

You need to add a password to the separate Samba password database. Use the following for each user and change security = share to security = user.

darrell@squall-ubuntu:/etc/samba$ sudo smbpasswd -a darrell
[sudo] password for darrell:
New SMB password:
Retype new SMB password:
darrell@squall-ubuntu:/etc/samba$  [/QUOTE]Just to clarify this statement. For **security = user** to work does not require a separate samba password unless you require authentication. And you certainly never have to create one for the local login user as your example indicates unless your remote user is authenticating with your user name.

It's true that you need to set up a local server user account and a corresponding samba password for every remote user that you want to authenticate before gaining access to the share, but you could for example have nothing but public shares which would not require any samba passwords to be created.

---

### Post by capscrew on 2010-01-23
> **Morbius1 said:**
> Just to clarify this statement. For **security = user** to work does not require a separate samba password unless you require authentication. And you certainly never have to create one for the local login user as your example indicates unless your remote user is authenticating with your user name.

As Samba is a client server protocol, the samba daemon always interacts with a client.  The Samba.org manual [**_[COLOR="Navy"]in this section[/COLOR]_**]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559296") clearly states this.
> 
It's true that you need to set up a local server user account and a corresponding samba password for every remote user that you want to authenticate before gaining access to the share, but you could for example have nothing but public shares which would not require any samba passwords to be created.

Whether remote or or local the client needs to be authenticated if you use **security = user**.

In my network the authenticated users have their information stored in the Gnome Keyring, so they never have to login after the first time.

Have I misunderstood your statement?

---

### Post by windyweather on 2010-01-23
So where does all this complexity leave netbook users?

How does this all compare with using a windows netbook with a windows network?

Are they comparably easy to setup?

This is my point about the OOTB experience.

Many folks want windows file sharing to be authenticated don't they? And with windows this is trivial and it works OOTB.

Doesn't Ubuntu need to be the same equivalently easy experience OOTB?

Geee... Maybe not if we want to keep Linux in it's marginalized position in the computer community.

- ww

---

### Post by capscrew on 2010-01-24
> **windyweather said:**
> So where does all this complexity leave netbook users?

I am no apologist for Microsoft, but since you asked...

This leaves Samba/Gnome/Linux/Debian/Ubuntu behind Microsoft's Windows7 I'm afraid.  But then again the open source community has nowhere near the focus or resources. Just look at all the different entities needed to bring the functionality you have now to Ubuntu 9.10 vs the one entity that is Microsoft.  
> 
How does this all compare with using a windows netbook with a windows network?

Microsoft is the leader of CIFS.  The possibilities have been further advanced with Windows 7  ***homegroup***.  See [**_[COLOR="Navy"]here [/COLOR]_**]("http://windows.microsoft.com/en-us/windows7/products/features/homegroup")for the hyperbole.  More technical thoughts on HomeGroup can be found [**_[COLOR="Navy"]here[/COLOR]_**]("http://blogs.msdn.com/e7/archive/2008/12/30/at-home-with-homegroup-in-windows-7.aspx").  > 

Are they comparably easy to setup?

Not at this point, I'm afraid.> 

This is my point about the OOTB experience.

Many folks want windows file sharing to be authenticated don't they? And with windows this is trivial and it works OOTB.

Doesn't Ubuntu need to be the same equivalently easy experience OOTB?

Not necessarily.> 

Geee... Maybe not if we want to keep Linux in it's marginalized position in the computer community.

- ww

Marginalized?  That is a pretty negative way of looking at the situation.  I prefer to think of it as an *exclusive *community.  Made up of enlightened individuals looking for alternatives to the mainstream.  I prefer to *roll my own *, thank you very much.  

Frankly I think the allegiance of most is due to price and not technical excellence.  New Linux users seem to start due to the expense of Microsoft products.  If MS gave away their OS product there would be an even smaller installed base of Linux users.

---

### Post by Morbius1 on 2010-01-24
> **capscrew said:**
> Have I misunderstood your statement?
I believe so.
> Whether remote or or local the client needs to be authenticated if you use security = user.You are absolutely correct. However....

Let's say I have a server with a mix of public and private shares. I have not created any accounts for remote client users nor have I created any samba passwords.
In this scenario, when any client identifies itself to the server it will be be viewed by the server as a "Bad User" and the ubuntu default "map to guest = Bad User" will convert all clients to "guests". Access to public shares will be accepted, access to private shares will prompt for authentication in an infinite loop since there is nothing to authenticate against. 

The original statement that "To use samba setting security = user you ***must***: .... add a password to the separate Samba password database" is incorrect since I may by design have only public shares on my server. You only need to create a samba password for those clients requiring access to private shares and you would never create one for yourself as the server login user unless you want clients to access your shares using your username.

---

### Post by Morbius1 on 2010-01-24
> **windyweather said:**
> Geee... Maybe not if we want to keep Linux in it's marginalized position in the computer community.

Which "computer community"?

On the desktop I suppose it is marginalized.

In the enterprise it is not. The majority of backend servers, application servers, and webservers are linux. Samba wasn't created for you and I to share files in our home network. It was created for the enterprise who can hire people to administer and configure it and presumably know way more about it that I do.

---

### Post by capscrew on 2010-01-24
> **Morbius1 said:**
> I believe so.
You are absolutely correct. However....

Let's say I have a server with a mix of public and private shares. I have not created any accounts for remote client users nor have I created any samba passwords.
In this scenario, when any client identifies itself to the server it will be be viewed by the server as a "Bad User" and the ubuntu default "map to guest = Bad User" will convert all clients to "guests". Access to public shares will be accepted, access to private shares will prompt for authentication in an infinite loop since there is nothing to authenticate against. 

The original statement that "To use samba setting security = user you ***must***: .... add a password to the separate Samba password database" is incorrect since I may by design have only public shares on my server. You only need to create a samba password for those clients requiring access to private shares and you would never create one for yourself as the server login user unless you want clients to access your shares using your username.

Yes you are correct.  I was concentrating on network users and not the guest account.  I actually use the guest mapping to map to the user ***smbguest***.

---


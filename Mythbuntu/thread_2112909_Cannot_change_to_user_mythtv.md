---
title: "Cannot change to user mythtv"
date: 2013-02-06
forum: Mythbuntu
---

### Post by gga96 on 2013-02-06
[FONT=Tahoma]Hi All,[/FONT]
 
[FONT=Tahoma]I am new to linux, migrating from window!!![/FONT]
 
[FONT=Tahoma]I am also new to mythbuntu, have downloaded and installed 10.04.1 - 32bit, it was a clean install.[/FONT]

 
[FONT=Tahoma]My user name is glen.[/FONT]
[FONT=Tahoma]The home directory has two subdirectories glen and mythtv. I assume that mythtv is a second user.[/FONT]

 
[FONT=Tahoma]Living in Australia I need to use shepherd for the EPG data. The reference [/FONT][[FONT=Tahoma]http://svn.whuffy.com/[/FONT]]("http://svn.whuffy.com/")[FONT=Tahoma] and [/FONT][[FONT=Tahoma]http://svn.whuffy.com/wiki/Installation[/FONT]]("http://svn.whuffy.com/wiki/Installation")[FONT=Tahoma].[/FONT]
 
[FONT=Tahoma]When I ran wget 'http://www.whuffy.com/shepherd/shepherd' the file was written to glen directory, so I tried to change to user mythtv but failed to provide the correct password for mythtv.[/FONT]
 
[FONT=Tahoma]Google searches seemed to indicate the user mythtv password was mythtv, but that failed. I used my user glen password and that also failed.[/FONT]
 

[FONT=Tahoma]What do I do to execute the shepherd installation. [/FONT]
 

[FONT=Tahoma]I will be grateful for any help you can muster.[/FONT]
 

[FONT=Tahoma]Thanks Glen.[/FONT]

---

### Post by furything on 2013-02-06
you don't need to use the mythtv account for epg

As you are correctly seeing the .mythtv folder holds the channel logos and your epg

If you followed the instructions correctly then I believe what has happened is you configure myth for no grabber.

Run the perl script which asks you questions and allows you to correctly configure your channels against the appropriate tv guide for that channel.

If you go back into myth tv backend are icons displayed against your channels?

Have you go into the front end and tried to open the tv guide?
run ```
mythfilldatabase
``` from a terminal and check the tv guide
Post the results of command here.

---

### Post by topcat5 on 2013-02-06
> **gga96 said:**
> 
[FONT=Tahoma]When I ran wget 'http://www.whuffy.com/shepherd/shepherd' the file was written to glen directory, so I tried to change to user mythtv but failed to provide the correct password for mythtv.[/FONT]
 
[FONT=Tahoma]Google searches seemed to indicate the user mythtv password was mythtv, but that failed. I used my user glen password and that also failed.[/font]

Issuing
```

sudo su - mythtv

```Will allow you to switch user to mythtv by entering your own password.  This assumes sudo is setup properly for your main ID. The "-" is optional.  The difference means you assume mythtv's environment. "exit" returns you to the previous ID

If that doesn't work then you can issue this:
```

sudo su 
passwd mythtv
exit

```This allows you to change mythtv's PW to whatever you like. You can then just log onto the ID.

---

### Post by furything on 2013-02-06
This detracts from the point YOU DON'T NEED TO LOGON as mythtv.

I am using the uk grabber and have done since about Dapper as a mythbuntu distro after trying things like mythdora.

Older versions were a lot more involved in getting things to work but at 12.04 things just tend to work without too much fiddling.

Other than using the mysql mythtv account to logon to mysql (not the linux logon account) I NEVER use the mythtv account.

Permissions to access mythtv files/folders are normally mythtv group which your user (in this case glen) is part of that group.

mythtv channel icons and program guide should end up in user glen not mythtv

Don't play around with the mythtv account otherwise you may totally break the system and have to rebuild.

---

### Post by nickrout on 2013-02-08
rubbish you can log in or switch to mythtv user and do plenty of stuff without screwing the system.

---

### Post by furything on 2013-02-08
> rubbish you can log in or switch to mythtv user and do plenty of stuff without screwing the system.Yes I expect you can but equally if you are unsure of what you are doing you can break it as well.

How often do you use the mythtv account?

I do everything from my user account and the system is also a webfilter so not just a simple myth back end. I reiterate there is no real need to use mythtv account.

I know I have in the past when I was trying to figure things out and yes I broke my system but I also fixed it.

---

### Post by topcat5 on 2013-02-08
> **furything said:**
> This detracts from the point YOU DON'T NEED TO LOGON as mythtv..You are offering up your opinion of what he needs based on your experience of a completely different process to retrieve schedule data.   

IMO, I'd rather give him the info he asked about, the Mythtv PW, and let him figure out what is appropriate for his particular installation.  

You are certainly entitled to your opinion, but so are the rest of us.

---

### Post by furything on 2013-02-08
> You are certainly entitled to your opinion, but so are the rest of us.
Agreed :rolleyes: did not mean to rant

---

### Post by gga96 on 2013-02-11
Hi to both furything and topcat5,
 
Thank you for your comments. Both comments are informative.
 
I have ordered another tuner that should arrive in about 10 days time. When it does I will install and config myth and report on this forum how I get on the second time around.

---

### Post by gga96 on 2013-03-03
I have now fixed the problem.

Installed fresh MythBuntu 12.04 and used [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme) to provide a driver for quad tuner [http://www.digitalnow.com.au/product_pages/Quad.html](http://www.digitalnow.com.au/product_pages/Quad.html).
The ambrosa make is currenty limited to kernel 3.0.0 .. 3.2.0.

Thanks for your interest.
Glen

---


---
title: "can I access shared windows folders on xubuntu 9.10?"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by branko.savic on 2010-04-24
I have a desktop pc running Windows 7 and a netbook running xubuntu 9.10 (Freshly installed!)

I am a total linux noob, so please go easy with me! :)

What I am trying to do is to access the shared folders on my windows 7 pc on my xubuntu netbook!

Please tell me that this is duable and hopefully it is easy!? :)

---

### Post by branko.savic on 2010-04-24
Did I put this in the wrong forum or is it that no one can answer?

Thanks!

---

### Post by suryaccnamcse on 2010-04-25
Yes, you can access windows shared folders on Linux. You have to install samba on the Linux computer, configure Samba to access the shares.

---

### Post by soropi on 2010-04-25
I think I had the same problem once and post for a solution , so have a look on this:
[http://ubuntuforums.org/showthread.php?t=1387871](http://ubuntuforums.org/showthread.php?t=1387871)
though it didn't help me much.

---

### Post by branko.savic on 2010-04-25
> **suryaccnamcse said:**
> Yes, you can access windows shared folders on Linux. You have to install samba on the Linux computer, configure Samba to access the shares.

Ok, now I have samba installed! Now what?
How do I configure it to see my shared folders from the windows machine?

---

### Post by branko.savic on 2010-04-25
> **soropi said:**
> I think I had the same problem once and post for a solution , so have a look on this:
[http://ubuntuforums.org/showthread.php?t=1387871](http://ubuntuforums.org/showthread.php?t=1387871)
though it didn't help me much.

You are right, that didnt help! Thanks for helping tough!

---

### Post by P4man on 2010-04-25
Im surprised this doesnt work out of the box on xubuntu (then again I havent tried xubuntu in ages). Anyway a quick google throws this:
[http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-and-windows-sharing-632963/](http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-and-windows-sharing-632963/)

maybe that helps (last post)? 

If not, a much more complicated solution here:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing](http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing)

But I dont know how up to date that still is...

---

### Post by branko.savic on 2010-04-25
> **P4man said:**
> Im surprised this doesnt work out of the box on xubuntu (then again I havent tried xubuntu in ages). Anyway a quick google throws this:
[http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-and-windows-sharing-632963/](http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-and-windows-sharing-632963/)

maybe that helps (last post)? 

If not, a much more complicated solution here:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing](http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing)

But I dont know how up to date that still is...

Thanks, but those instructions are a little hard to follow! (I am a complete noob with linux!) :(

Is there not just a program I can start and then just click on "network" and access my shared folders?

Windows has that function, why would linux be any different?

Thanks!

---

### Post by Gunman1982 on 2010-04-25
> **branko.savic said:**
> Windows has that function, why would linux be any different?

*coughs* Did you ever try to access shared folders between different Windows versions? :-P

And maybe a small thing to think about: If you want an operating system that behaves like Windows you should probably stay with Windows. Linux isn't Windows.

However, when you click on Places->Network and so on you should see the shared folders of your windows machine (as long as it is accessible by the linux machine and samba is installed).

---

### Post by branko.savic on 2010-04-25
> **Gunman1982 said:**
> *coughs* Did you ever try to access shared folders between different Windows versions? :-P

And maybe a small thing to think about: If you want an operating system that behaves like Windows you should probably stay with Windows. Linux isn't Windows.

However, when you click on Places->Network and so on you should see the shared folders of your windows machine (as long as it is accessible by the linux machine and samba is installed).

Yes I have accessed folder between windows machines, and it was pretty easy!

When I click on places I have no network or anything similar at all! 
Maybe I am missing some components? I have samba installed!

I know linux is not windows, I know how to operate windows, now I want to learn linux! Starting small with network access! :)

---


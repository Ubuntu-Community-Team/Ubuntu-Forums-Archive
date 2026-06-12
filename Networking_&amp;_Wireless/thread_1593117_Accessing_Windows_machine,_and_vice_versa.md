---
title: "Accessing Windows machine, and vice versa"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-10-11
I had a look through a tutorial video showing how to set up Samba, and the end result was the only shared file/folder showed up on Windows. I want a direct access to all the files and folders like you can do from Windows to Windows, by signing in the user account from another system. And likewise I want access to all Ubuntu files and folders of a user account through Windows.

Please tell me how if it's possible with or without Samba.

Thanks for your help!

---

### Post by atworkwithjf on 2010-10-11
Have you considered using Likewise-Open?  If you're using AD for user authentication, etc. you would pretty much be able to do all this with AD/NFS and Samba.

Liekwise Open is in the standard repository but there is a much newer version on the project homepage.  It's open source and works great, allowing you to consolidate user management and UID's in your environment.

[http://www.likewise.com/products/likewise_open/](http://www.likewise.com/products/likewise_open/)

The current version is 6.0 and the version in the apt-get repo is 5.4 I think.  Their open source forums also have a lot of tips on what you want to do.

Personally I'd use NFS to export the stuff you want the *nix machines to access (home dirs, etc.).  If you have Windows Server 2008 or newer you should be able to do this out of the box and performance should be better than Samba.

- atworkwithjf

---

### Post by Oxwivi on 2010-10-12
Care to detail some instructions? Admittedly, I'm new to the technical stuff, and failed to interpret less than the quarter of all those abbreviations you mentioned. I'm still learning, so any help will be greatly appreciated.

---

### Post by SlugSlug on 2010-10-12
windows > ubuntu -- install openssh on ubuntu & use winscp on windows to access it

ubuntu > windows -- mount the drive.. [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by atworkwithjf on 2010-10-12
[Oxwivi]("http://ubuntuforums.org/member.php?u=1131907"),

There are a number of ways to accomplish what you want to do.  

Perhaps a better way to start would be to describe what you want to accomplish, etc.

Do you want centralized home directories and centralized authentication and management for your user accounts?  

Do you have any security auditing requirements?  

Do you use Active Directory in your environment?   NIS?  LDAP?  Anything for centralized user management?

Do your users interact with a large volume of data and if so do you want them storing that data in common project based locations or do you want to allow them to save things in their home directories (generally a bad idea if users need to collaborate)?

Once we have a better understanding of your needs I'm sure a suitable solution will be more obvious.

As I said, there are a number of ways to do what you are looking to accomplish, many of them right, but depending on what you need to accomplish, some solutions will be better suited than others.

---

### Post by Oxwivi on 2010-10-12
atworkwithjf, thank you, but I'm not looking for some serious stuff, it;'s just a home network. My PC is the only one with Ubuntu, but the HDD is just 10GB. What I'm looking for is to just access the entire HDD of the system's on my network or at least one user profile so I can store and retrieve files for the Windows system.

I tried networking with XP and 7 before using Ubuntu, and I could log in to one of the user accounts of one system from the another. Something similar or access to the entire HDD is what I'm looking for.

Thank you for your concern and help.

---

### Post by atworkwithjf on 2010-10-12
Probably the best way to do this without getting into to much complication (which would clearly be overkill given your needs) would be to use Samba to share a common filesystem where all your user data would reside.

Seems you have little or no need to enforce complicated user access policies or security so this may be the most efficient path forward for you.

---

### Post by Oxwivi on 2010-10-13
For that I need instructions for the reasons I mentioned in my second post.

And there's another thing. My desktop is connected to wireless like I mentioned and also an ethernet card. I have another desktop to which I wish to give access to internet with wire using my first computer. I made it possible to share internet that way while using XP, and I'm sure there's also a way to do the same with Ubuntu. Should I make a new thread about it?

---

### Post by Morbius1 on 2010-10-13
I would caution you against sharing your entire home folder especially if this is a laptop or other mobile device where you will at some point leave the security of being behind your router. But that's up to you.

The easiest way is to approach this as if you were sitting in front of a Windows machine. Let's say I wanted to share /home/morbius1:

Open Nautilus and go to /home
Right Click morbius1 and select "Sharing Options"
Select "Share this folder"
Select "Allow others to create and delete.." ( if that's want you want )
Select "Guest Access" ( I wouldn't do that on a drunken bet but that's up to you )
Select "Modify Permissions"

You will get the following error:
> 'net usershare' returned error 255: net usershare add: share name morbius1 is already a valid system user name
You need to change the share name ( which will be highlighted in red ) to something other than "morbius1" - like morbius1home

To require a username and password to access the share don't select "Guest Access". You will then have to create a local user and then a samba password for the remote user to use to access your share. Or you can completly throw caution to the wind and set up a samba password for yourself and have the remote user access your share using your username.

As for doing this to your entire install ( not just your home directory ) - that's just wrong :wink:

---

### Post by Oxwivi on 2010-10-13
No one at home except me have anything to do with Ubuntu or Linux, and there's nothing I have to hide, so I don't care the extent of what I share on the Linux system. But my main concern is accessing the Windows system so I can use it as some sort of external storage system because as I mentioned my Ubuntu system is only 10 GB.

So how do I access Windows system with Samba or any other solution?

And what of sharing internet that I mentioned in my last post?

---

### Post by Morbius1 on 2010-10-13
>  So how do I access Windows system with Samba or any other solution?Nautilus > Network
>  And what of sharing internet that I mentioned in my last post?     Never done it, sorry.

---

### Post by Oxwivi on 2010-10-13
Oh hey, the Windows system shows up on the Network folder on Nautilus, how do I access it's folders?

---


---
title: "File and Printing Share Question"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by HaVoK-69 on 2010-03-21
Hello, I just installed Ubuntu 9.1 on this system fresh with the live cd it being the only OS on the hard drive. I have a 2nd desktop PC with Windows 7 Ultimate 32 bit and I would like to know how I would be able to set up file sharing and printer sharing across the network with the different Operating Systems. The printer is a Lexmark X4200 Series if that matters and I would like to set up shares to different directories of my external hard drives on the windows 7 machine. I am very experienced with windows systems and currently attempting to learn more about linux but I know a fair amount about the OS. Looking forward to what you got to say. Thanks.

---

### Post by AgentZ86 on 2010-03-21
> **HaVoK-69 said:**
> Hello, I just installed Ubuntu 9.1 on this system fresh with the live cd it being the only OS on the hard drive. I have a 2nd desktop PC with Windows 7 Ultimate 32 bit and I would like to know how I would be able to set up file sharing and printer sharing across the network with the different Operating Systems. The printer is a Lexmark X4200 Series if that matters and I would like to set up shares to different directories of my external hard drives on the windows 7 machine. I am very experienced with windows systems and currently attempting to learn more about linux but I know a fair amount about the OS. Looking forward to what you got to say. Thanks.

It's pretty straight forward, to share files just like in windows.

Right click the folder you want to share and click properties / share tab

Or, just right click and select Share Options.

And if you share your Windows files then it's similar to make sure you work group is the same on both machines it makes things simpler

And if you select Places/Network it's also very simple as well.


But I personally like smb4K because it has more features and works a little better with being able to (save and save-as to the network share) Standard sharing with the 2 options above has some limitation which you might not even notice, but if you want to save as for certain files or open with then those 2 options become a little more limited, but smb4k does not have these types of limits and more server-ish.
Just install that from Applications/Ubuntu Software Center, and type smb4k in the search bar, and install it.

Then you can easily set up your workgroup name from there:
When you open smb4k just go to settings/configure smb4k
On the left select Samba and put in your Workgroup name where is says domain

And then select Authentication and put in your credentials there, user and pass if you made one for your windows shares.

Then just browse in smb4k the tab at the bottom that says network neighborhood

You can setup a wallet to have one login for all server and share credentials.

And lastly you can also just right click

---

### Post by km0r3 on 2010-03-21
@AgentZ86:
Is Samba pre-installed on Ubuntu 9.10?

@HaVoK-69:
I suggest using Samba if you want to share your files with Windows workstations.

Helpful links:

[LIST]
[*][https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[*][http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[*][http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
[/LIST]
Please also try a Google query with keywords like "Ubuntu Samba Setup" or "Ubuntu Samba File Sharing" or [be creative]..

Also using the Forum search might spit out some useful results, too. :)

---

### Post by AgentZ86 on 2010-03-23
> **km0r3 said:**
> @AgentZ86:
Is Samba pre-installed on Ubuntu 9.10?

@HaVoK-69:
I suggest using Samba if you want to share your files with Windows workstations.

Helpful links:

[LIST]
[*][https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[*][http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[*][http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
[/LIST]
Please also try a Google query with keywords like "Ubuntu Samba Setup" or "Ubuntu Samba File Sharing" or [be creative]..

Also using the Forum search might spit out some useful results, too. :)

Hi

Yes Karmic 9.10 has samba installed by default, but typically for simple file sharing and print sharing I don't think you really even need that , but it makes things simpler.


See this article too:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by HaVoK-69 on 2010-03-24
Thanks you both for the quick responses. I will try your suggestions and am sure I will be able to figure this out now. Thanks again.

---


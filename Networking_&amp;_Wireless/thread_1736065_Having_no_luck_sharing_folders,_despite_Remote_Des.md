---
title: "Having no luck sharing folders, despite Remote Desktop working"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by demonboy on 2011-04-22
I'm confused. I have a wireless network enabled that three computers are members of. They can see each other because I can Remote Desktop between all three of them, which can only mean they are part of the same local network. They connect through this network and not externally through internet connection. They all run Ubuntu 10.10.

So why can I not share files?

When I run through the usual Share folder procedure the host computer displays the correct icon to show that they are being shared. When I run 'shares-admin' they come up. The properties show that the folders are shared through Windows networks (SMB) because I have Samba installed. Samba is installed on all three machines. Under General Properties the domain is 'workgroup' and the 'this computer is a WINS server' is unticked. As for the Users tab I get confused so I don't touch this.

When I run 'gksudo nautilus' and inspect the folders in question they too are shared. They show the 'shared' icon. If I right-hand mouse click and go to 'sharing options' all boxes are ticked including 'allow others to create and delete files in this folder' and 'guest access'.

Whilst in sudo Nautilus if I click the properties of the shared folder and go to Permissions I note that only the Owner has 'create and delete' permission. The Group (name of that computer) and Others have no folder access and when I try and change them from 'Folder Access: None' to 'Folder Access: Create and Delete Files' it won't let me. Is this my problem? How come I can't change these even though I sudo'd Nautilus? Do I have to change permission via CLI rather than GUI? I'm not good with command line stuff. For example I have taken a look at this [how-to set up NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") but I get really uncomfortable with command-line instructions and don't understand it. I need a GUI alternative.

The other problem I am having is that when I select Network from my Places menu I see the Windows Network icon but when I click on it it comes up with the 'Unable to Mount' error. Is this related to the other problem? Also I cannot see any other computer on the network.

The help pages and tutorials make it sound really simple. Just 'share' and they should appear. Why don't they then? I'm sure there is something really simple I am overlooking but after spending 24 hours on this I cannot work out what the problem is.

Any help appreciated.

[edit]
I have since found out some additional things which are supposed to have helped, but haven't. I had to go to System/Preferences/Personal File Sharing. None of the simple how-tos on file sharing in Nautilus that I read told me this. Then you come across this bug as outlined [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/536766"). This was reported over a year ago and is still an issue. So after installed apache2.2 and the other file the 'share folders' was no longer greyed out. However the correction as per Morbius's post in this [thread]("http://ubuntuforums.org/showthread.php?t=1502265#8") still does not not correct the problem.

Still confused.

[an hour later]
Found that the firewall on my host machine doesn't help. Even so, disabling it does not resolve the issue. It allows me to click on the host machine via my client machine but it displays no shared folders or files. Kinda getting really angry with this. I have spent my whole Good Friday on this and have made very little progress. Spent most of the day searching and reading other threads and it seems to be a common problem. Sharing files is one area where Ubuntu's strap-line "it just works" does not apply. Why is file sharing on Ubuntu so convoluted?

---

### Post by demonboy on 2011-04-22
After 15 hours I found a solution. The only thing in favour of my frustration is the fact that this is a well documented problem. That is, well documented in terms of people having problems with file sharing. The solution was less well documented.

Anyway, I was put out my misery via a step-by-step process written two years ago that still seems to apply. The only thing I would add is that I ended up disabling my firewall altogether, which I'm entirely happy about since I connect via a dongle and not a router. 

Props to Dmizer for [the solution]("http://ubuntuforums.org/showthread.php?t=1169149").

Phew.

---


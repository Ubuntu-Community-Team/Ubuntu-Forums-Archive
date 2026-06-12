---
title: "&quot;Unison&quot; for peer to peer wireless hookup"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by algrossi on 2011-12-30
I must love the punishment, after 15 years of not touching Unix, I chose to install Ubuntu on an old Dell laptop, dual booting with Windows XP. 
Then I I also installed it on a Compaq laptop, dual booting with Windows 7. 
Now I am trying to network them for file sharing using Unison. Since I have a peer-to-peer wireless LAN, the IP addresses are assigned dynamically, so setting up the /etc/hosts file for host name resolution is useless, since the IP addresses could differ every time I boot up. 
Using static IP would create collisions when my wireless printer or my daughter's laptop comes on the scene. 
As I said, I love the punishment, but at this point I am tripping over the same issue, with no idea how to move forward. 
Does anyone know of a "wizard-like" tool which would help in such a situation? 
I don't want to give up this scenario because it's  a great way to keep all my files in synch.
Well punished! Al 
:confused:

---

### Post by gordintoronto on 2011-12-30
I've never heard of Unison, but I can guarantee that you don't need it to share files. By the way, it is always useful to mention which version of Ubuntu you are using.

In the Nautilus file manager, you could create a folder to hold shared files. Then right-click on the folder and select "sharing options." Click on "Share this folder," give it a name and also click on "Allow others..." and "Guest access". You might be prompted to install Samba, depending on which version you are using. The installation might be automatic, then start again at "right click," above.

From the other computer, in the file manager, click on Network, double-click on "Windows Network," the Workgroup name, the computer name, the share name. You should see the list of files. You can also copy a file into the shared folder.

There are probably 100 versions of these instructions online, which you could have found with Google.

---

### Post by algrossi on 2011-12-30
Sorry for the lack of info, I am using the Nautilus 2.30.1 File Manager and the Ubuntu version is 10.04 LTS Lucid Lynx.
Since this File Manager supports shared folders, I will take that approach. The greater issue is trying to network to the other peer machine running Ubuntu. But as you say, Samba may do the trick. I have Samba installed so I will keep reading up about the tools I have rather than trying to bring in another one. Trying to configure Unison was driving me crazy.
Thank you for the help;
AL

---


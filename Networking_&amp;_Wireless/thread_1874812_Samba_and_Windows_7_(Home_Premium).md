---
title: "Samba and Windows 7 (Home Premium)"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by stephen67 on 2011-11-03
I am trying to get simple file sharing working.

I am failing. :(

I am using Ubuntu 11.04.

I have completed the setup based on the how-tos. And I have tried to find solutions with Google, but I get so many links that do not address my issue.

1) On the Windows 7 machine, I see the Ubuntu computer, but when I click to see the shared directories, I get a dialog wanting a User Name and Password. It also mentions the domain (which is the same as the computer name). I have specified in Windows to use Workgroups. I have shared on the Ubuntu machine (right click directory in Nautilus, and share allowing guest access). I have tried using a cmd net share and also get the credentials prompt. How do I fix this?

2) On the Ubuntu box, in Nautilus, I open the Networks folder, and I see the Workgroup. I click on it, but after time passes, I get an error saying it cannot be mounted, I am thinking that I should at least see the Ubuntu computer and the local shares. Note: I did set the workgroup in smb.conf. How do I fix this?

Thanks in advance!
Stephen

---

### Post by vandamme on 2011-11-04
Well, I came here looking for an answer, but I seem to have gotten further than you did. Have you shared anything on Ubuntu? Go to places->home->Public, right click, sharing options, then click everything on and put a file in the folder. When I do that I can see the file from the Windoze machine. I use the 'network" not the Homegroup, which only connects Win7. Now, I'm trying to see folders on the win7 machine from ubuntu...."Failed to retrieve share list from server"  :confused:

---

### Post by Raventat on 2011-11-20
> **vandamme said:**
> Well, I came here looking for an answer, but I seem to have gotten further than you did. Have you shared anything on Ubuntu? Go to places->home->Public, right click, sharing options, then click everything on and put a file in the folder. When I do that I can see the file from the Windoze machine. I use the 'network" not the Homegroup, which only connects Win7. Now, I'm trying to see folders on the win7 machine from ubuntu...."Failed to retrieve share list from server"  :confused:

Hi vandamme,

I had that same error as well "Failed to retrieve share list from server".  It turned out that I did not have smbfs (samba file system) installed, which I added in with Synaptic.  After that I rebooted and was able to access Win7 shares just fine.

Now if I could just figure out how to add Ubuntu as a network computer within Win7:confused:

---

### Post by SeijiSensei on 2011-11-20
What if you try connecting to \\ip.of.ubuntu.server, e.g., \\10.10.10.10?

---


---
title: "Viewing other computers on network"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by mrogovin on 2013-03-03
Besides my lubuntu machine, I have a Win7 PC, and Seagate NFS, all three on a wired network, and occasionally a Macbook on Wireless. In my original linux install (Mint Cinnamon) these were all automatically visible when I clicked on Places/Network in the file manager. But Cinnamon was too slow for my old PC. However, in other DEs in Mint, and now in Lubuntu, they are not visible. Note that I have installed smbclient. Here is the output of the smbtree command:

WORKGROUP
            \\ARAGORN       Den
MIDDLE EARTH
            \\GALADRIEL     Seagate BlackArmor NAS

When I select Go Network in the File Manager, I get an icon for Windows Network. Clicking on that eventually produces 3 file folders after a delay: one without a name, one WORKGROUP and one MIDDLE EARTH, but clicking on any of these produces error messages after a long delay:

first: Failed to received share list from server, then The specified location is not mounted

I have read other similar threads, but none had a solution that seemed applicable to my situation.

---

### Post by tgalati4 on 2013-03-03
What other DE's in Mint are you referring to?  Perhaps Linux Mint MATE would work.  Nautilus and Caja (MATE's version of Nautilus) is probably what you want to browse network shares.  Thunar may not see all of the shares from newer machines.  Make sure that you have the same user name account on each machine and that you have properly set up the WORKGROUP names in the File Sharing Properties.

---

### Post by mrogovin on 2013-03-03
I tried Mate, LXDE, and others. Nautilus saw the files, but some dialog boxes within other programs could not. My machine needs a very lightweight DE because it is an older (Pentium 4, 1GB RAM) that otherwise runs Windowsxp, albeit slowly. Thought that a lightweight Linux would work better than Windows, but it has been nothing but trouble from the day I started installing different variants. Mate did not work. Only Cinnamon in fallback mode worked (but too slowly for practical use). I am testing LUbuntu now, not Mint. As for user accounts, I want to access different shares on each machine. If Lubuntu can't read network shares, I will have to abandon it too.

---

### Post by GregA on 2013-03-04
With 1 gb of ram, it's worth a try to run Kubuntu as the KDE file managers (dolphin & konqueror) seem to do a decent job on finding fat/nfts on wired and wireless networks.   Also, if you do try Kubuntu, you'd want to go into the system settings dialogs and disable any desktop effects, and turn off file search & indexing (nepomuk) - - thereby speeding up KDE considerably.

---

### Post by mrogovin on 2013-03-04
Thanks. I will take a look at Kubuntu. Trying to find the right distro for this older PC has consumed much more time than I anticipated, but I probably should have thought of that when dipping my toes into a new OS.

---

### Post by mrogovin on 2013-03-04
Installed Kubuntu, status is more confused than ever. 
1. Clicking on Network gives me the following icon shortcuts: Network, Network Services and Samba Shares. Network leads to icons for this computer, my file seerver and another desktop. But clicking further finds only servers running on those PCs (VLC Streamer on one, and the configuartion screen in a browser window for the file server). Shares do not appear. There is nothing in network services. In Samba Sahres, 2 workgroups appear, though they appear with only the first letter capitalized instead of all caps. Clicking in each one gets an error. It cannot open the share. (all the above in dolphin). In Konqueror, clicking one workgroup gets an error:
==============
[h=1][SIZE=1]The requested operation could not be completed[/SIZE][/h][h=2][SIZE=1]Improperly Formatted URL[/SIZE][/h][h=3][SIZE=1]Details of the Request:[/SIZE][/h]
[LIST]
[*][SIZE=1]URL: smb:/[/SIZE]
[*][SIZE=1]Protocol: smb[/SIZE]
[*][SIZE=1]Date and Time: Monday, March 04, 2013 07:45 PM[/SIZE]
[*][SIZE=1]Additional Information: smb:/[/SIZE]
[/LIST]
[SIZE=1]================
Clicking in the other (url smb:/workgroup/) gets a timeout error.

In Dolphin, both just keep trying to open with no result.

[/SIZE]

---


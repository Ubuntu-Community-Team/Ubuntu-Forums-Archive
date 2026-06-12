---
title: "Kubuntu Hardy box cannot host files through samba"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by FSHero on 2009-04-02
Greetings all,

I have a problem with Samba on one of my computers. First, let me describe the situation: I have three computers: a Medion desktop, a Mesh desktop and a Dell laptop. To simplifiy things, I'll now just refer to them as the Medion, the Mesh and the laptop.

The Medion runs Kubuntu 8.04 i386 (up-to-date with updates), running kernel 2.6.24-19. It also runs Windows XP 32-bit SP3. When I installed Kubuntu, I assigned it the computer name medion-p4.
The Mesh runs Kubuntu 8.04.2 amd64, running kernel 2.6.24-23. It also runs Windows Vista 32-bit SP1. When I installed Kubuntu, I assigned it the name mesh-c2q.
The laptop runs Kubutu 8.04 (up-to-date with updates), running kernel 2.6.24-23. It also runs Windows Vista 32-bit (SP1 I think). When I installed Kubuntu, I assigned it the name fshero-ins1525.

I installed the Mesh with a point release 8.04.2 cd. I think I installed the Medion and the laptop with an 8.04 or 8.04.1 cd.

Anway... the problem is that I cannot export or host (terminology correct?) files from the Mesh through Samba. When I installed Kubuntu on it, I installed a bunch of nfs and samba related packages; e.g. I have installed libsmbclient, samba, samba-common, smbclient, smbfs.

The Mesh computer has Windows Vista 32-bit SP1 installed. I want to share a folder containing my files to other computers. The folder containing everyone's documents is /media/data/documents

I created some shares in a way that I had previously done with the Medion and the laptop (which incidentally works on those): I went to K-menu --> System Settings --> Sharing (under network and connectivity). I clicked the File Sharing option on the left and clicked the Administrator Mode button.

The Medion and the laptop can access each others' files. e.g. on Medion, if I type in the address bar of Konqueror "smb://fshero-ins1525", I can see a MUSIC and a fshero-documents folder that I shared from an ext3 partition. If I type "smb://medion-p4" into Konqueror in the laptop, I can see the files and folders I shared off an NTFS partition. I can open and access these files in programs without any problem.

I shall describe the procedure I used to create shares on the **Mesh** computer:

To share /media/data/documents (which is on the NTFS partition) I clicked Add, then entered the folder in the box "Folder", checked the box "Share with Samba", and kept the default share name DOCUMENTS.

To share /home/fshero (my Home folder in Kubuntu), I did exactly the same, but give the name FSHERO to the share.

I also shared /tmp under the name "TMP" and /media/data/download (on NTFS partition) under the name "download". (I shared /tmp as a test.)

I tried to access the shares from my laptop with the following results:

In Konqueror, I type in smb://192.168.0.4. I can see the four folders.

Double-clicking on the DOCUMENTS and download folders leads to this error message: "The file or folder smb://192.168.0.4/xxx does not exist."  xxx  is the folder name.

If I go into the folder smb://192.168.0.4/FSHERO, I am actually able to see its contents and navigate its directory structure. However, I try to open a script file in Kate I get the error message:

"Could not read smb://192.168.0.4/FSHERO/treeview.sh.".

I get a similar error message when I try to open a GIMP .xcf file.

Interestingly, I have a file called packages.txt (the output of dpkg --get-selections which I tried for fun!) in the "FSHERO/for-sharing" folder that I can open perfectly. I also have an .ogg and .mp3 file that can play perfectly!

If I go into the folder smb://192.168.0.4/TMP, I am also able to navigate that also.

The Mesh computer's ability to access files from the (for example:) laptop is perfect. It can 

Therefore... what's going on? Why can't I share out files that are on the NTFS partition? Why can't I access .xcf and .sh files but can access .txt, .ogg and .mp3 files that are stored on the Mesh?

Unfortunately, I haven't had a chance to test the Mesh's ability to access the files on the Medion, however I assume that it's okay.

Please help!

Attached: my Mesh computer's /etc/samba/smb.conf

---


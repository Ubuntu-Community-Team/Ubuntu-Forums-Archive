---
title: "Installing Postfix2.6 in Ubuntu8.04"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by harika_paddu on 2009-05-18
Hi There,
 ):P
I would like to install Postfix-2.6.0 in Ubuntu 8.04. 
 
This is a Proxy server and Inernal Firewall in my company. I am not be able to install the Postfix. Becauase i am a beginner to Ubuntu and Postfix.
 
Can any one help me that how to install Ubunutu. 
 
This computer is not connecting to internet at the present. What I did is, i have downloaded "**Postfix 2.6.0** into my Laptop , copied the Postfix file to Ubuntu proxy server. 

**Here, The file is in "postfix-2.6.0.tar.gz', then i have extracted this into a folder on the desktop.**

**The problem is, i am not able to install postfix file which is copied on the desktop.**

**could any one please tell me that" How to install the Post fix. The file is on the desktop. what is the path or commond to install this post fix file.**
 
Thank you
Harika_paddu:popcorn:

---

### Post by chili555 on 2009-05-18
Please try this:```
cd Desktop/postfix-2.6.0
make
sudo make install
```There are some specific dependencies that are easy to resolve *IF* you have internet capabilities:> If you can't compile Postfix because the file "db.h" isn't found, then you MUST
install the Berkeley DB development package (name: db???-devel-???) that
matches your system library.However, if you have internet capabilities, it will be easier to simply:```
sudo apt-get install postfix
```Please post back when you get stuck.

---

### Post by chili555 on 2009-05-18
[http://packages.ubuntu.com/hardy/postfix](http://packages.ubuntu.com/hardy/postfix)

---

### Post by harika_paddu on 2009-05-18
> **chili555 said:**
> [http://packages.ubuntu.com/hardy/postfix](http://packages.ubuntu.com/hardy/postfix)
Dear chili555,
 
I have the Postfix File on the Folder with the Name of"postfix-2.6.0". and i have also have one postfix file on the desktop named as "postfix-2.6.0.tar.gaz".
 
Now , I have followed above steps given by you. as follows:
 
 
step1:i have typed     [COLOR=red]**cd Desktop/postfix-2.6.0**[/COLOR]
**[COLOR=#ff0000][COLOR=#808080]Result is:[/COLOR]        [/COLOR][COLOR=red][EMAIL="administrator@zzproxy:~/Desktop/postfix-2.6.0"]administrator@zzproxy:~/Desktop/postfix-2.6.0[/EMAIL][/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=dimgray]step2: i have typed as [/COLOR][COLOR=red] make[/COLOR]**
**[COLOR=#696969]Result is: [/COLOR][COLOR=blue]make -f makefile.in MAKELEVEL=Makefiles[/COLOR]**
**[COLOR=#0000ff] (echo "# Do not edit -- this file documents how Postfix was built for your machine."; /bin/sh makedefs) >makedefs.tmp[/COLOR]**
**[COLOR=#0000ff]/bin/sh:can not create makedefs.tmp:permission denied[/COLOR]**
**[COLOR=#0000ff]make: *** [makefiles] Error 2[/COLOR]**
**[COLOR=#0000ff]make: *** [makefiles] Error 2[/COLOR]**
**[COLOR=#0000ff][EMAIL="administrator@zzproxy:~Desktop/postfix-2.6.0"]administrator@zzproxy:~Desktop/postfix-2.6.0[/EMAIL][/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
**[COLOR=dimgray]step3: i have typed as [/COLOR][COLOR=red]sudo make install[/COLOR]**
**[COLOR=dimgray]result is:[/COLOR][COLOR=blue] [sudo] password for administrator:**********[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
**[COLOR=#0000ff]please review the INSTALL instructions first.[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
**[COLOR=#0000ff][/COLOR]** 
**[COLOR=purple]Now, I am stuck with this from 4 days. [/COLOR]**
[COLOR=#800080]**i do not have inernet connection for this machine to use the command "**[COLOR=#000000]sudo apt-get install [/COLOR][/COLOR][COLOR=#ff0000]**postfix". so can not use thsi command without internet connection.**[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][COLOR=#000000] [/COLOR]
[[COLOR=#444444]http://packages.ubuntu.com/hardy/postfix[/COLOR]]("http://packages.ubuntu.com/hardy/postfix") this link is not helpful for me.
 
 
Could you please help me to install Postfix . 
 
I hope that some one will help me as soon as possible.
 
Thank you
 
Harika Paddu
[/COLOR]

---

### Post by chili555 on 2009-05-18
> make: *** [makefiles] Error 2When you get this, there is no reason to continue. You can't build a package with broken parts.

I think your error tells us that there are multiple dependencies missing; *build-essential* and *linux-headers*, for example. Rather than go out and download these to another computer, install them, find that they have more dependencies, etc., let's just try to get the Ubuntu-versioned postfix.

I have been searching for a definitive list of what is on the installation CD and have not found it. I suspect, but can't be sure, that postfix is there. Please drop the CD in the tray and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install postfix
```It will complain when it can't find the on-line repositories, but it will probably install postfix and its dependencies.

---

### Post by harika_paddu on 2009-05-18
> **chili555 said:**
> When you get this, there is no reason to continue. You can't build a package with broken parts.

I think your error tells us that there are multiple dependencies missing; *build-essential* and *linux-headers*, for example. Rather than go out and download these to another computer, install them, find that they have more dependencies, etc., let's just try to get the Ubuntu-versioned postfix.

I have been searching for a definitive list of what is on the installation CD and have not found it. I suspect, but can't be sure, that postfix is there. Please drop the CD in the tray and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install postfix
```It will complain when it can't find the on-line repositories, but it will probably install postfix and its dependencies.
Hi chiki555,
 
Thank you for the quick reply. Now I have tried with CD as below:
 
**sudo apt-cdrom add**
[COLOR=blue]using CD-ROM mount point /cdrom[/COLOR]
[COLOR=blue]Unmounting CD-ROM[/COLOR]
[COLOR=blue]waiting for disc...[/COLOR]
[COLOR=blue]Please insert a Disc in the drive and press enter[/COLOR]
[COLOR=blue][/COLOR] 
////(Here, i have pressed enter)
 
[COLOR=blue]MMounting CD-ROM...[/COLOR]
[COLOR=#0000ff]identifying....[some no came here][/COLOR]
[COLOR=#0000ff]scanning disk for index files.[/COLOR]
[COLOR=#0000ff]Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures[/COLOR]
[COLOR=#0000ff]This disc is called[/COLOR]
[COLOR=#0000ff]'Kubuntu 8.04.1 Hardy Heron_ -Release i386(20080701.2)'[/COLOR]
[COLOR=#0000ff]copying package lists...gpgv:Signature made Wed 02 jul 2008 07:19:07 EST using DSA key ID ....[/COLOR]
[COLOR=#0000ff]gpgv:good Signature from Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"[/COLOR]
[COLOR=#0000ff]Reading Package Indexes...Done[/COLOR]
[COLOR=#0000ff]Writing new source List[/COLOR]
[COLOR=#0000ff]Source List Entries for this disc are:[/COLOR]
[COLOR=#0000ff]deb cdrom:[Kubuntu 8.04.1_Hardy heron_- Release i386 (20080701.2)]/ hardy main restricted[/COLOR]
[COLOR=#0000ff]Unmounting CD-ROM...[/COLOR]
[COLOR=#0000ff]Repeat this process for the rest of the CD in your set.[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=purple]Now,** I have typed as     [COLOR=darkorange]sudo apt-get update[/COLOR]**[/COLOR]
**[COLOR=darkorchid]   Result is: E:Type '/home/administrator/Desktop/postfix-2.6.0' is not known on line 57 in source list  /etc/apt/sources.list[/COLOR]**
**[COLOR=#9932cc][/COLOR]** 
**[COLOR=darkorange]now,  i have typed as    [/COLOR][COLOR=darkred]sudo apt-get install postfix[/COLOR]**
**[COLOR=#8b0000][/COLOR]** 
**[COLOR=darkgreen]_the Result_ is:[/COLOR]**
**[COLOR=#006400]E: Type '/home/administrator/Desktop/postfix-26.0' is not known on line 57 in source list /etc/apt/sources.list[/COLOR]**
**[COLOR=#006400]E:The list of sources could not found be read.[/COLOR]**
**[COLOR=#006400][/COLOR]** 
**[COLOR=#006400][/COLOR]** 
**[COLOR=#006400][/COLOR]** 
**_[COLOR=magenta]I am requesting you that could you please help me to install this postfix .[/COLOR]_**
**_[COLOR=#ff00ff][/COLOR]_** 
**_[COLOR=#ff00ff]I hope that you or some one will help to fix this probelm. [/COLOR]_**
**_[COLOR=#ff00ff][/COLOR]_** 
**_[COLOR=#ff00ff]As i am new to this, i can not complete this task in my company since from yesterday.[/COLOR]_**
**_[COLOR=#ff00ff][/COLOR]_** 
**_[COLOR=#ff00ff]Than you for your Help[/COLOR]_**
**_[COLOR=#ff00ff][/COLOR]_** 
**[COLOR=#ff00ff]Best Regards[/COLOR]**
**[COLOR=#ff00ff]Harika_paddu[/COLOR]**

---

### Post by chili555 on 2009-05-19
> Result is: E:Type '/home/administrator/Desktop/postfix-2.6.0' is not known on line 57 in source list /etc/apt/sources.listThis means that the list *apt* reads from has a faulty entry. I suggest you do:```
sudo gedit /etc/apt/sources.list
```When your cursor is at the top of the page, you will see 'LN1, COL 1' in the lower right. You will therefor be at line 1. Go down to line 57 and remove the line that reads:```
/home/administrator/Desktop/postfix-2.6.0
```Proofread, save and close gedit. Then rerun:```
sudo apt-get update
sudo apt-get install postfix
```

---

### Post by harika_paddu on 2009-05-19
> **chili555 said:**
> This means that the list *apt* reads from has a faulty entry. I suggest you do:```
sudo gedit /etc/apt/sources.list
```When your cursor is at the top of the page, you will see 'LN1, COL 1' in the lower right. You will therefor be at line 1. Go down to line 57 and remove the line that reads:```
/home/administrator/Desktop/postfix-2.6.0
```Proofread, save and close gedit. Then rerun:```
sudo apt-get update
sudo apt-get install postfix
```
Hi Chili555,
 
Thank you for your information and help. This time aslo unsuccessfull. no luck yet. it is still not working. I have tried as above instructions. The result as follows:
 
step1: i have typed [COLOR=red]**sudo gedit /etc/apt/sources.list**[/COLOR]
[COLOR=dimgray]Result is: [/COLOR][COLOR=red]**sudo:gedit: command not found**[/COLOR]
 
**[COLOR=slategray]step2[COLOR=darkorange]:[/COLOR][/COLOR][COLOR=darkred]/home/administrator/Desktop/postfix-2.6.0[/COLOR]**
**[COLOR=slategray]Result is:[/COLOR][COLOR=#8b0000]/home/administrator/Desktop/postfix-2.6.0 is a directory[/COLOR]**
 
[COLOR=slategray]**_step3_**[/COLOR] :[COLOR=darkgreen]**sudo apt-get update**[/COLOR]
 
[COLOR=slategray]**_Result is_**[/COLOR]: **[COLOR=darkgreen]E:Type [/COLOR][COLOR=darkgreen]'/home[/COLOR][COLOR=darkgreen]/administrator/Desktop/postfix-2.6.0' is not known on line 57 in source list /etc/apt/sources.list[/COLOR]** 
 
step4 : sudo apt-get install postfix
[COLOR=slategray]**_Result is_**[/COLOR]: **[COLOR=darkgreen]E:Type [/COLOR][COLOR=darkgreen]'/home[/COLOR][COLOR=darkgreen]/administrator/Desktop/postfix-2.6.0' is not known on line 57 in source list /etc/apt/sources.list [/COLOR]**
**[COLOR=#006400]E: The List of sources could not be read.[/COLOR]**

**_[COLOR=magenta][/COLOR]_** 
**_[COLOR=magenta]*This time aslo unsuccess full installation? again fail ? i am really disoppointed because of *[/COLOR]_**
**_[COLOR=magenta][/COLOR]_** 
**_[COLOR=magenta]*Postfix can not be installed!!*[/COLOR]_**

 
[COLOR=indigo]So Now also , **i will not be able install Postfix-2.6.0 on Ubuntu.**[/COLOR]
**[COLOR=#4b0082]I am struggling to install postfix-2.6.0[/COLOR]**
 
**[COLOR=#4b0082]Could you please help me to install this Postfix as soon as possible. i have to install this postfix as soon as possible. I have did lot of search and research on "How install Postfix" , but no use.[/COLOR]**
 
**[COLOR=darkred]I hope that you will help me to install Postfix as soon as possible[/COLOR]**
 
**[COLOR=#8b0000]Thank you[/COLOR]**
 
**[COLOR=#8b0000]best Regards[/COLOR]**
**[COLOR=#8b0000]Harika Paddu[/COLOR]**

---

### Post by chili555 on 2009-05-19
> step1: i have typed sudo gedit /etc/apt/sources.list
Result is: sudo:gedit: command not foundIf you get that far and don't succeed, there is no need to continue.

Step 2 was to remove the quoted line from the */etc/apt/sources.list* file, not to run it as a command.

You might try:```
sudo nano /etc/apt/sources.list
```and then proceed as I outlined.

Please check your private messages.

---

### Post by harika_paddu on 2009-05-19
> **chili555 said:**
> If you get that far and don't succeed, there is no need to continue.
 
Step 2 was to remove the quoted line from the */etc/apt/sources.list* file, not to run it as a command.
 
You might try:```
sudo nano /etc/apt/sources.list
```and then proceed as I outlined.
 
Please check your private messages.
[COLOR=darkred]**sudo nano /etc/apt/sources.list**[/COLOR]
 
this line only works [COLOR=dimgray]OK[/COLOR]. I have removed the **[COLOR=#8b0000]/home/administrator/Desktop/postfix-2.6.0 [/COLOR][COLOR=dimgray]in Line 57 manually and save and exit. But the below things are not working OK.[/COLOR]**


**[COLOR=#696969]Then , i have typed [/COLOR]**
 
[COLOR=red]**_sudo apt-get update_**[/COLOR]
 
[COLOR=red]**Result is as below:**[/COLOR]
 
[COLOR=red]**Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy release.gpg**[/COLOR]
[COLOR=red]**could not resolve 'au.archive.ubuntu.com'**[/COLOR]
[COLOR=red]**//like this there are different error about 10 lines //**[/COLOR]
 
[COLOR=red]**W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release/gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release/gpg) Could not resolve 'au.archive.ubuntu.com'**[/COLOR]
 
[COLOR=red]**there are some similar lines of messages under this.**[/COLOR]
 
[COLOR=red]**[COLOR=darkgreen]Then I have typed as [/COLOR][COLOR=darkgreen]_sudo apt-get install postfix_[/COLOR]**
[/COLOR]**[COLOR=#696969]Result is as follows:[/COLOR]**
**[COLOR=darkgreen]Reading package lists....done[/COLOR]**
**[COLOR=#006400]Building dependency tree[/COLOR]**
**[COLOR=#006400]Reading state information...Done[/COLOR]**
**[COLOR=#006400]Package postfix is not available,but is referred to by another package. [/COLOR]**
**[COLOR=#006400]This may mean that the package is missing , has been obsolated, or [/COLOR]**
**[COLOR=#006400]is only avaialble from another source.[/COLOR]**
**[COLOR=#006400]E:package postfix has no installation candidate[/COLOR]**
 
**[COLOR=darkred]I have treid as [/COLOR][COLOR=#006400]_sudo apt-get install /home/administrator/Desktop/postfix-2.6.0_[/COLOR]**
 
**[COLOR=#006400]this also not working[/COLOR]**
 
**[COLOR=darkred]I have aslo tried sudo apt-get instal postfix-2.6.0[/COLOR]**
 
**[COLOR=#8b0000]this is also not working[/COLOR]**
 
**[COLOR=purple]Finally, i have eneded up with the unsuccessfull postfix installation.[/COLOR]**
**[COLOR=#800080]could you please suggest me any alternative solution.[/COLOR]**
 
**[COLOR=#800080]Note: I have two files on the desktop . One file name is: _postfix-2.6.0_ (this is a postfix folder file which is extracted from zip file)[/COLOR]**
 
**[COLOR=#800080]Second file name:_postfix-2.6.0.tar.gz_[/COLOR]**
 
 
**[COLOR=#696969]could you please help me.[/COLOR]**
 
**[COLOR=#696969]Thank you[/COLOR]**
 
**[COLOR=#696969]best Regards[/COLOR]**
**[COLOR=#696969]harika Paddu[/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]Hi chili555 , [/COLOR]**
**[COLOR=#696969]i have added you for msn and yahoo too.[/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]My msn id is "balu-love143"[/COLOR]**
**[COLOR=#696969]my yahoo is"balaraju_engineering".[/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]please accept the request. [/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]please help me.[/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]I will be online at 9 am -5pm sydney, Australia Time.[/COLOR]**
**[COLOR=#696969][/COLOR]** 
**[COLOR=#696969]Thank you[/COLOR]**

---

### Post by chili555 on 2009-05-19
All your problems would be solved if you could get internet access even for ten minutes. Can't you drag the machine to an ethernet jack for a while?

To install from the files you have on your desktop requires dependencies you don't have, but could get easily with internet access.

To install from apt requires internet access, because the packages are not on the CD.

---


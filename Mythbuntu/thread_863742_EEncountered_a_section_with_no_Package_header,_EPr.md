---
title: "E:Encountered a section with no Package: header, E:Problem with MergeList"
date: 2008-07-18
forum: Mythbuntu
---

### Post by jabrown65 on 2008-07-18
I am using mythbuntu 8.04 with all updates install (... until this probolem occured this morning...)

However, when I tried to to update using the Update-Manager I got the following error message:

[B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

I tried replacing ../status with ../status-old but the problem remained.

Then I tried apt-get check just to see what would happen, and I basically got the same error:

[B]jbcp@mythbuntu:~$ sudo apt-get check
[sudo] password for jbcp: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
jbcp@mythbuntu:~$ [/B]

What next?

---

### Post by jaakan on 2008-07-18
try 
# sudo dpkg --configure -a
# sudo aptitude update
# sudo aptitude upgrade

you can use apt-get too but I think aptitude is better.

look here too if that doesn't work
[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)

---

### Post by jabrown65 on 2008-07-19
The dpkg command didn't help. I still get the same error msg when I execute the aptitude (or apt-get) update command.

Other ideas?

---

### Post by jabrown65 on 2008-07-19
Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

---

### Post by whoey on 2009-07-17
that worked a treat for me too!

---

### Post by p_breakfast on 2009-08-11
Thanks! also worked under GUbuntu 9.04

---

### Post by olly_roberts on 2009-08-27
+1 success here.
cheers.
i do like this ubuntu malarchy, this is the 3rd "issue" ive had, but unlike windows, they are all so easy to sort!

---

### Post by charlesedwardkelley on 2009-09-07
Thanks
sudo rm /var/lib/apt/lists/* -vf
Did the trick for me

---

### Post by amksep on 2009-09-23
solved here too.
Ubuntu 9.04
but i wish to know the cause of it.

---

### Post by mihai.ile on 2009-09-29
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

Worked for me too, I think synaptic should be patched to take care of this without any extra intervention for the user particular issue, as the fix is really straight forward.

---

### Post by Slide guitar on 2009-10-03
Thanks for that.
sudo rm...... followed by sudo apt-get.....
worked the oracle for me.

---

### Post by astathios on 2009-10-23
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

great worked perfect thank you

---

### Post by guriinii on 2009-10-27
Thanks worked a treat.

---

### Post by richard.scott-ettrick on 2009-10-29
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
Brilliant! Worked for me too!!
;)

---

### Post by jarrarist on 2009-11-05
worked like a charm!!

thanks

---

### Post by redcore on 2009-11-09
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
Worked for me too (Linux Mint 8) - Thanks! :)

---

### Post by Oleglit on 2009-12-03
oleg@ubuntu:~$ sudo apt-get update
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic Release.gpg [189B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:2 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/main Translation-ru [329kB]     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:4 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                      
&#1048;&#1075;&#1085; [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-ru             
&#1048;&#1075;&#1085; [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-ru                        
&#1048;&#1075;&#1085; [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-ru       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:5 [http://deb.opera.com](http://deb.opera.com) stable Release [1.067B]                        
&#1048;&#1075;&#1085; [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-ru         
&#1048;&#1075;&#1085; [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-ru       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:6 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [37,1kB]         
&#1048;&#1075;&#1085; [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
&#1048;&#1075;&#1085; [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:7 [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages [861B]                
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [22,8kB]   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [6.297B]   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [7.526B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [793B] 
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:16 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/restricted Translation-ru [4.099B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:17 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/universe Translation-ru [383kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:18 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/multiverse Translation-ru [20,9kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:19 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates Release.gpg [189B]     
&#1048;&#1075;&#1085; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/main Translation-ru         
&#1048;&#1075;&#1085; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/restricted Translation-ru      
&#1048;&#1075;&#1085; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/universe Translation-ru        
&#1048;&#1075;&#1085; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/multiverse Translation-ru      
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:20 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic Release [65,9kB]               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:21 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates Release [44,1kB]       
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:22 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/main Packages [1.353kB]        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:23 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/restricted Packages [7.971B]   
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:24 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/main Sources [640kB]           
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:25 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/restricted Sources [3.270B]    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:26 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/universe Packages [5.133kB]    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:27 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/universe Sources [2.795kB]     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:28 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/multiverse Packages [190kB]    
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:29 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic/multiverse Sources [116kB]     
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:30 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/main Packages [103kB]  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:31 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/restricted Packages [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:32 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/main Sources [30,8kB]  
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:33 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:34 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/universe Packages [60,8kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:35 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/universe Sources [13,3kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:36 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/multiverse Packages [1.616B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:37 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) karmic-updates/multiverse Sources [1.223B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086; 11,4M&#1041; &#1079;&#1072; 1&#1084;&#1080;&#1085; 31&#1089; (124k&#1041;/c)                                          
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1054;&#1096;&#1080;&#1073;&#1082;&#1072;!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: &#1057;&#1087;&#1080;&#1089;&#1082;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1080;&#1083;&#1080; status-&#1092;&#1072;&#1081;&#1083; &#1085;&#1077; &#1084;&#1086;&#1075;&#1091;&#1090; &#1073;&#1099;&#1090;&#1100; &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1099; &#1080;&#1083;&#1080; &#1087;&#1088;&#1086;&#1095;&#1080;&#1090;&#1072;&#1085;&#1099;.

---

### Post by ni_shi2005 on 2010-01-25
[B]me toooo!! mee toooo
i mean this thing " sudo rm /var/lib/apt/lists/* -vf " saved me too :)
[/B]

---

### Post by Dalston on 2010-01-26
Thanks this worked for me too.

---

### Post by markofealing on 2010-02-07
sudo rm /var/lib/apt/lists/* -vf

Thanks also worked for me on Kubuntu 8.10 and stopped my CPU hitting 100% utilisation with nothing running after failing to do an update.

---

### Post by captivus on 2010-07-05
Deleting the list cache didn't seem to work for me.  I actually had to restore my /var/lib/dpkg/status-old file, as it seemed mine was corrupt.  This fixed the problem, though:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgrade
```Cheers,

captivus

---

### Post by slotto on 2010-07-20
> **jabrown65 said:**
> Actually, just fixed the problem using:
<snip>


Thanks Bro!

---

### Post by SabreWolfy on 2010-11-13
Thanks. Removing the files worked for me too after a Lucid to Maverick upgrade.

---

### Post by wi0 on 2010-12-25
Me too (Ubuntu 10.10)! Thanks.

---

### Post by concept08 on 2011-01-09
[B]Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libgutenprintui2-1 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/B]

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
 sudo rm -f /var/lib/dpkg/lock

sudo rm /var/lib/apt/lists/* -vf
added to apt.conf.d 
APT::Cache-Limit="2516582";
sudo apt-get update && sudo apt-get upgrade

i have tried all of this and it does not seem to work for this problem
Ubuntu 10.04 LTS
                - the Lucid Lynx
updated firefox last night and today i cant install or update anything else.

thanks for the help

---

### Post by dimas11 on 2011-01-19
I am using Ubuntu 10.10 and _**rm**_ command did the trick for me as well. Thanks.

---

### Post by dimas11 on 2011-01-19
I am using Ubuntu 10.10 and _**rm**_ command did the trick for me as well. Thanks.

---

### Post by dimas11 on 2011-01-19
I am using Ubuntu 10.10 and _**rm**_ command did the trick for me as well. Thanks.

---

### Post by Gerroo on 2011-01-23
A BIG THANK YOU to you from Bahrain, worked here as well, long time after the firs post. Feals good to be back after many years of winscrap.

---

### Post by C64HCS on 2011-01-24
Yop, thank you so much captivus! Worked 100% for me.
;)


Cheers,
C64HCS

---

### Post by cooldamage on 2011-02-26
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.


Works great for me in Maverick Meerkat. 

=D> =D> =D> =D> =D>

---

### Post by r94851486 on 2011-04-02
Hi.. It worked for me too... :) :D Thx....:o

---

### Post by doogiekd on 2011-04-08
worked for me as well.

thanks!

---

### Post by Dutch70 on 2011-04-09
Still working in 11.04 beta!!! :D

---

### Post by daniel.s3000 on 2011-04-23
It didn't work for me, this is the error I was getting and I got it again after using the rm procedure and updating apt-get:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```


I'm using 11.04 Beta2

---

### Post by phifgo on 2011-04-23
It doesn't work 4 me too
Natty Beta 2
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.rootguide.org_ubuntu_dists_natty_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


---

### Post by haddog on 2011-04-23
Worked for me today also in 11.04/Natty Beta 2. Thanx!

---

### Post by phifgo on 2011-04-24
I had  to remove the rootguide repo from /etc/apt/source.list and it worked! thanks

---

### Post by narendraD on 2011-04-30
Used this method to be able to update my brand new install of 11.04 i386.

Any idea why this issue comes up.

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-05-01
that woked with me on ubuntu 11.04 natty i386 

but i've a question how could i get the log that contain my last problems ?

tahnk you very much

---

### Post by Tesla Trooper on 2011-05-01
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
worked like all above
in UBUNTU NN 11.04!!
that's turned into an "ancient bug" like these black ones from The Mummy movie!

---

### Post by tushargkwd on 2011-05-06
> Originally Posted by **jabrown65**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5415838#post5415838")                 
                 [I]Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
[/I][I]
------------------------------
Worked Like a Charm for me.......a big thanks to you !!!
[/I]

---

### Post by ghauff on 2011-05-14
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
thanks this worked ubuntu 11.04

---

### Post by quack on 2011-05-16
Interestingly the same fix solved the same problem for a Nokia N900.

I guess Maemo and Ubuntu aren't that many miles apart, and I love having a phone I can run apt-get on :-)

---

### Post by olof_ on 2011-05-17
problem solved for me too. Using Ubuntu 11.04

---

### Post by aduff on 2011-05-18
Worked for me too .....3 years after the original solution

---

### Post by dg4345 on 2011-05-20
Perfect! Thank you very much!!!:P

---

### Post by itbcn8 on 2011-05-21
worked for me!
Linux Mint Debian Edition.

Love Linux, problems always have a logical solution and the crowd-sourced knowledge of every distribution all help each other. :)

<3 u Ubuntu guys, even though LM is better ;) <3

---

### Post by lastbalance on 2011-05-22
It works. Thank you.

Ubuntu 11.04

---

### Post by dg4345 on 2011-05-24
It works, but every time I reboot my system I have the same problem. Any Ideas?

---

### Post by mnabeel on 2011-05-30
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

:)

Worked out for me too.

Three cheers. Thanks.

---

### Post by imurphy on 2011-05-31
worked for me too in ubuntu 11.04

---

### Post by skvivian on 2011-06-03
Has anyone found a more permanent solution to this? I've already increased the cache size, but it didn't seem to help.

---

### Post by shehzad on 2011-06-03
Deleting the lists files solves the problem, but still needs permanent solution.

---

### Post by livetobefree on 2011-06-03
Hello,

  I know that version 10.04 is no longer supported.  I did not update my system before it became unsupported (probably update in early April or late march?)  \
Anyway I went to update and I encountered problems installing packages, heres what I got;

Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon



I cannot at this time update or upgrade from the UPDATE MANAGER at all.      

I have read several theards, but none that seemed to be directed at version 10.04

any advice would be great.

---

### Post by tgm4883 on 2011-06-03
> **livetobefree said:**
> Hello,

  I know that version 10.04 is no longer supported.  I did not update my system before it became unsupported (probably update in early April or late march?)  \
Anyway I went to update and I encountered problems installing packages, heres what I got;

Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon



I cannot at this time update or upgrade from the UPDATE MANAGER at all.      

I have read several theards, but none that seemed to be directed at version 10.04

any advice would be great.

10.04 is LTS, and supported for 3 years on the desktop and 5 years on the server. You still have another year of support. Are you getting the error message in the title of this thread? If not, you need to open a new thread.

---

### Post by skvivian on 2011-06-04
> **livetobefree said:**
> Hello,

  I know that version 10.04 is no longer supported.  I did not update my system before it became unsupported (probably update in early April or late march?)  \
Anyway I went to update and I encountered problems installing packages, heres what I got;

Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon



I cannot at this time update or upgrade from the UPDATE MANAGER at all.      

I have read several theards, but none that seemed to be directed at version 10.04

any advice would be great.

I think your problem is different. This thread is focused on a problem with apt, not dpkg. The dpkg parse error message you posted does seem to hint at what you might try correcting, though.

---

### Post by vanquishedangel on 2011-06-05
Hi, This fixed worked great in Lubuntu 11.04 Thank you for the posting of it.

---

### Post by wamarobert on 2011-06-10
.:: According to my books the update-manager had broken down and needed to be patched...hence the code.

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

R. Bakyayita

---

### Post by Demetris Tziambazis on 2011-06-11
DIdnt worked for me... :( damn!! 
got: "E: Unable to locate package update"

anyone?? newbie here! got 11.04

---

### Post by akannankeril on 2011-06-11
worked for me in ubuntu 11.04! thanks!

---

### Post by nits. on 2011-06-14
finally apt-get is working! and so is update manager.

sudo rm /var/lib/apt/lists/* -vf

worked for me too...11.04
thanks!

---

### Post by Imachin on 2011-06-18
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Bullseye!! It worked on Ubuntu 11.04 USB Live!!!

Thanks a lot

---

### Post by jimfromtexas on 2011-06-18
works on debian too!
Thanks

---

### Post by chopurtito on 2011-06-21
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

thank you so much, problem solved!!!!!

---

### Post by Kralnor on 2011-06-24
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

Worked for me in Ubuntu 11.04. Thanks!

---

### Post by alesha on 2011-06-25
worked for me too! Ubuntu 11.04

Thank you very much!!

---

### Post by S1gurd on 2011-07-15
I am running 10.04 server, and this was a difficult scenerio.  I started with an old HP DX2200 PC, which I have never espeically liked, but it is what I have to work with.  Couldn't get a boot CD to work because of a proprietary memory problem involving failure of the RAMDISK, and the work around was to plug the drive into another machine and use Clonezilla to snap the image on, then move the drive back.   All worked just fine until it was time to update the box.  I got the errors described above.  Following the advice in this thread and another one I got it to work this way:    

  sudo rm /var/cache/apt/*.bin 
  sudo rm /var/lib/apt/lists/* -vf 

Had to run both prior to update and upgrade.  Working well now.  Thanks for all of your help.

---

### Post by fabiolus on 2011-07-19
Hey thanks for the help - solved the same issue on 10.10 Maverick Meerkat

---

### Post by Shad3y on 2011-07-21
Thank you it worked for me too, i been trying to fix this problem for ages.....thanks :)

---

### Post by littelbro14 on 2011-08-10
Worked perfectly for me on 11.04! Thank you!

---

### Post by pulencio on 2011-09-01
it worked for me... thanks!

---

### Post by blackplague1347 on 2011-09-08
Never had this problem before, but 

```
sudo rm /var/lib/apt/lists/* -vf
```took care of it. 

Thanks!

(11.04)

---

### Post by T_u on 2011-09-24
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

Worked wonders (Ubuntu 11.04)!

Thanx!

---

### Post by $war00p on 2011-10-15
Worked like a charm in ubuntu 11.04 too! thanks. But why did this happen?

---

### Post by lwfitz on 2011-11-04
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
 
Perfect! Thank you!

---

### Post by epayen on 2011-12-23
Thank you all!! These solved my problem too:


> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

You are unique! Merry Christmas.

---

### Post by gsumners on 2011-12-25
Solution still works on Linux Mint 12, which is based on Ubuntu 11.10 - thanks much!

---

### Post by ESDEEM on 2012-02-19
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
It worked bro..! It worked...
thanks in advance !

---

### Post by brons2 on 2012-05-03
> **jaakan said:**
> try 
# sudo dpkg --configure -a
# sudo aptitude update
# sudo aptitude upgrade

you can use apt-get too but I think aptitude is better.

look here too if that doesn't work
[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)

Using these commands with apt-get fixed this same problem with my 12.04 installation.  Thanks!

---

### Post by sasciame on 2012-05-21
Is there a more permanent solution to this?  I wind up having to do this (sudo rm /var/lib/apt/lists/* -vf ) at least once per day.


lubuntu 12.04

---

### Post by mungatsuma on 2012-05-30
> sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

This worked like a charm on ubuntu 12.04. Thank you guys.

---

### Post by al090187 on 2012-06-03
Hi,

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The above commands do solve the problem temporarily, but like other people, it happens again most days, and usually with different package lists.

Does anyone know the reason these Package Headers aren't in the right places? It is starting to get annoying. Then we can get a permanent fix for this.

Thanks

---

### Post by Fiuzer on 2012-06-07
> **jaakan said:**
> try 
# sudo dpkg --configure -a
# sudo aptitude update
# sudo aptitude upgrade

you can use apt-get too but I think aptitude is better.

look here too if that doesn't work
[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)


Thank you!

just Use:

# sudo dpkg --configure -a
# sudo apt-get update
# sudo apt-get upgrade

---

### Post by brent_watson on 2012-06-18
Same thing on 12.04

```
sudo rm /var/lib/apt/lists/* -vf
```

worked for me.

---

### Post by Nebay on 2012-06-23
> **jabrown65 said:**
> actually, just fixed the problem using:

Sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

all good now.


thank you!!! <3

---

### Post by mreipr on 2012-06-24
Thank you, thank you you save my sanity !....
rm /var/lib/apt/lists/* -vf worked for me too !!  :p

---

### Post by dailywalk365 on 2012-06-24
Thanks, My Ubuntu is now up to date.  Just a quick addition, if anyone is using Virtualbox and cannot update, make sure your network adapter in the Virtualbox control panel it set to BRIDGED.  The new version of Virtualbox sets new VM Guests to NAT by default.

---

### Post by Superman1504 on 2012-07-13
Hey guys.  I'm running ubuntu 12.04 on my old HP G60.  I'm getting an error with the "No Hash Entry Release" deal.  I tried:

# sudo dpkg --configure -a
# sudo apt-get update
# sudo apt-get upgrade

and I tried

  	 	 	 	 	 	   sudo rm /var/lib/apt/lists/* -vf  and I tried using aptitude but it still isn't working.  Here is the code:

superman1504@superman1504-HP-G60-Notebook-PC:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                                                           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb InRelease                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                     
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                                                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources                                                                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games i386 Packages                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games TranslationIndex                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en_US                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 4 B in 4s (0 B/s)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.


Any feedback would be appreciated.

Thanks!

---

### Post by pegasusgr on 2012-09-11
> **jabrown65 said:**
> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.
Still works in 12.04! Cheers!

---

### Post by leopd on 2012-09-16
I have this exact problem:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.



And I have followed all the instructions (s) given on this thread and others. However, it has NOT solved the problem. 

The last lines in the terminal folowing partial update are:

...
 Fetched 18.5 MB in 1min 21s (227 kB/s)                                         
W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid InRelease: File /var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Index](http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.



ARE THERE OTHER SUGGESTIONS PLEASE, It's really important as I think it's why Firefox is frequently crashing.

---

### Post by tgm4883 on 2012-09-16
> **leopd said:**
> I have this exact problem:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.



And I have followed all the instructions (s) given on this thread and others. However, it has NOT solved the problem. 

The last lines in the terminal folowing partial update are:

...
 Fetched 18.5 MB in 1min 21s (227 kB/s)                                         
W: GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid InRelease: File /var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Index](http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/repository.cairo-dock.org_ubuntu_dists_intrepid_cairo-dock_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.



ARE THERE OTHER SUGGESTIONS PLEASE, It's really important as I think it's why Firefox is frequently crashing.

This has nothing to do with firefox crashing. Further, your issue with those entries could be that cairo-dock.org appears to no longer exist (which is why it't not downloading anything from there). I suggest you open a new thread for your firefox issue.

---

### Post by tgm4883 on 2012-09-16
Locking thread as its run its course. All new posts are either "fixes it for me too" or unrelated. Due to the nature of the issue and the resolution for it, it will also fix it in the future releases as it literally is deleting corrupt files and redownloading them.

---


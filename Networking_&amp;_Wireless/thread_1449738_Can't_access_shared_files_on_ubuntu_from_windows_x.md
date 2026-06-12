---
title: "Can't access shared files on ubuntu from windows xp"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-04-08
When I first start up my 2 computers once the network is established if I try to acces the Ubuntu shared folders from the Win XP machine I get this error:
"\\localhost is not accessible.  You might not have permission to use
this network resource.  Contact the administrator of this server to find
out if you have access permissions.  You were not connected because a
duplicate name exits on the network.  Go to System in Control Panel to
change the computer name and try again."
If I first access the Windows shared files and then go back to the Win machine I get the password prompt and all is well.
Is this normal?

---

### Post by Morbius1 on 2010-04-08
I don't know if that's normal behavior but I do know that your Ubuntu box needs a name. Every box by default has a name of localhost so the network is confused about who's who.

By far the easiest way to give your Ubuntu box a name so Samba is happy is to use Samba itself:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
netbios name = put_your_desired_machine_name_here
```Save smb.conf, exit gedit, and back in the Terminal type: **sudo service samba restart**

Note: Make sure your machine name is 15 characters or less or Windows has a conniption :)

---

### Post by Silvertones on 2010-04-08
Yes I've done all of that like this:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

Maybe I just need to wait for them to communicate to each other. If I immediately try to connect to the Windows machine first everything is fine.

---

### Post by Morbius1 on 2010-04-08
Just curious. Did you have problems with file sharing that you had to resort to that HowTo?

---

### Post by Silvertones on 2010-04-08
Yes if I recall. Originally I was just right clicking on a file in Nautilus and say ing to share. Sort of like in Windows. I found this how to and it works well as long as a first connect to the Win machine from the Ubuntu machine. This is the part I'd like to figure out.
Do you have an issue with that tutorial?

---

### Post by Morbius1 on 2010-04-08
I really don't take issue with it per se ( although I'll admit that every time I read in a HowTo that all the worgroup names HAVE to match - it does make me wince. :) ) it's just that I find the default smb.conf will work unless there are other networking issues.

I don't know if I've ever come across a situation like yours. If it just didn't work that would be one thing but you situation is odd.

[COLOR=Blue]EDIT: I wonder if there is a conflict with the method you tried to use ( nautilus-share ) and the one you're using now.[/COLOR]

Open a Terminal and issue the following command: **net usershare info**
See if your sharing the same target directory using two different methods.

Nautilus-share and Classic-share ( what you're using now ) are two completely different methods and are configured in two different places.

---

### Post by Silvertones on 2010-04-08
That command issued no info. I did set up the shares via smb.conf
I don't even see the Ubuntu computer in My Network Places on the XP machine.
I had to re run the network wizard on the windows machine to get the Ubuntu machine to show in My Network Places. I think it's a Windows issue myself. I used to have this same sort of issue when  both machines were  Windows and when it was Nautilus & Windows. That's what got me searching for the Samba tutorial. The thing about the Samba setup is I always am able to get connectivity between the 2 machines. I just have to use the bookmark to the windows share first. It's not that big a deal as these machines sit side by side on my desk. Sort of my Super computer. Linux on the Internet Windows for my proprietary music programs. With file & printer sharing.
I'm just trying to figure it out.

---

### Post by Morbius1 on 2010-04-08
What you could do is run some commands from WinXP. They might produce error messages that can be investigated.

In WinXP, run **Command Prompt** and issue the following command:

**net view**

You should get a listing of all the machines on your network like this:

> Server Name            Remark 
 ------------------------------------------------------------------------------- 
\\MAYA                  
\\MIXTEC               
 Then, based on the previous output you can run the following command:

**net view \\maya **

> Shared resources at \\maya 
 
 Share name   Type         Used as  Comment 
 
------------------------------------------------------------------------------- 
D            Disk 
E            Disk 
HP           Print 
The command completed successfully.
It won't fix anything, it's basically the Windows equivalent of **smbtree** command. But it might yield some error messages that you can post back or search for.

Run these commands before you do anything else so that you can get the errors before it resolves itself.

---

### Post by Silvertones on 2010-04-09
Sorry i shut off the computers at 6:00 EST
OK on initial boot on the Win machine when I first run net view I get " There are no entries in the list" if I wait a moment I get 
Server Name      Remark
----------------------------------------------
\\BOBO

This is Windows computer

Wait a few more minutes and I get: " system error 6118 has occurred" & " The list of servers for this workgroup is not currently available"

Wait a couple minutes:

\\BUBBLES-UBUNTU
\\BOBO

This is both computers

Wait a few minutes and I get the same errors as above.

Connect to the win machine from the ubuntu and then try to connect to the Ubuntu and I get the pasword prompt. I log in then" net view" in command prompt and I get:
\\BOBO
\\BUBBLES-UBUNTU

Wait a few minutes and errors are back with "net view" however I have no problems sharing files or folders or printers even though the errors come and go over time.

---

### Post by Morbius1 on 2010-04-09
I looked through my notes and this is most likely a windows firewall problem not allowing Samba ports to be open.

The other possible cause is a service on Windows called: [FONT=Verdana]**Computer Browser Service** not running[/FONT].

It's the transient nature of you description that has me bewildered. Either the firewall is blocking samba or it isn't for example. I don't understand how it could work one minute and then not work the next.

Sorry , I don't have an answer.

---

### Post by capscrew on 2010-04-09
> **Morbius1 said:**
> I looked through my notes and this is most likely a windows firewall problem not allowing Samba ports to be open.

The other possible cause is a service on Windows called: [FONT=Verdana]**Computer Browser Service** not running[/FONT].

It's the transient nature of you description that has me bewildered. Either the firewall is blocking samba or it isn't for example. I don't understand how it could work one minute and then not work the next.

Sorry , I don't have an answer.

The only thing I can think of is the Browse Master refreshing.  For this to work properly either DNS or NetBIOS needs to function correctly.  There are really 2 daemons working here. There is **nmbd ** as well as **smbd**.

It is true that Windows does use a NetBIOS helper nowadays and that should be always be running on the Windows hosts unless you are in a public place.  The recent Windows hosts use port 445 rather than the older 139.

**Edit:** I wonder what the system logs and samba logs have in them.

---

### Post by Silvertones on 2010-04-09
Ain't the firewalls cause the windows one is off and I've tried turning off the GUFW one on Ubuntu and no difference.
Listen folks don't get to involved. As long as I access the windows machine first in the AM it's perfect all day long.
It was just a weird thing.

---

### Post by Silvertones on 2010-04-09
OK now I feel like a real idiot. Oh well I've only been at the Linux thing for a couple of months. I learned this lesson on another issue but seem to have forgotten. I disabled the Firewall in Ubuntu BUT did not reboot. This time I disabled the GUFW and rebooted both machines. I tried to access the Ubuntu machine from Windows and it worked this time. I got the sign in box and voila. It was the GUFW blocking the access.

---

### Post by Silvertones on 2010-04-09
:)So you ask why was the UFW blocking access? The answer is simple. I'm 60 years old and when I dumped my WUBI install a couple weeks ago I had to resetup the UFW and I type the rules in backwards. I redid them and I'm fine.

---

### Post by Silvertones on 2010-04-09
What rule do I need to put in to UFW to allow the windows computer access to the Ubuntu printer?

---

### Post by Morbius1 on 2010-04-10
Windows should be using samba as a pass-through to the CUPS printing system. So if you have normal file sharing working then it should see your Linux printer if you have it enabled so. If it were a linux - linux printer share you would need to allow port 631.

Make sure your linux attached printer is shareable:

*Enable Sharing for that Printer.*
Administration > Printing > Right Click the attached printer > Properties > Policies - Check Enabled, Accepting Jobs, and Shared

*Enable Publishing of the Shared Printer*
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

I'm not fluent in linux firewalls because I don't use one. I'm behind a router so I don't feel the need for a firewall behind a NAT router. No one from the WAN can see my machine from behind the router. I have one on my windows machines but that's not to prevent something from coming in, it's to prevent something from going out.

---


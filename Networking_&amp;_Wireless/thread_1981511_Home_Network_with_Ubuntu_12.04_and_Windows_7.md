---
title: "Home Network with Ubuntu 12.04 and Windows 7"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by walt11 on 2012-05-16
I'm running Ubuntu 12.04 on my desktop with Ethernet connection, and Windows 7 (64 bit) on my laptop with wireless. They are connected to the router (DSL) provided by my ISP, so am uneasy about changing settings. I would like the systems to be able to communicate in several ways: I'm running XAMPP servers on both systems, and want to be able to ftp between them. Also would like to be able to share files between the systems outside the server environment.

(My Ubuntu is on an external drive which can be booted from the laptop. The desktop would then be running XP SP3. But that's not my usual configuration.)

If you reply, start out at a basic level. My understanding of networking and associated terminology is limited. --Thanks.

---

### Post by dandnsmith on 2012-05-17
I suggest you start by a google search, as I know there are several expositions for the comparative novice on how to set this up.

Both Ubuntu and Windows support 'shares' - but don't get suckered into setting up a HomeGroup on Windows7, as this cannot communicate with anything except Windows7.

---

### Post by walt11 on 2012-05-18
Thanks. I appreciate your advice. (When I first booted Windows 7 a year ago I was given the option of setting up a HomeGroup. Not knowing any better, I did - but my laptop is the only member, and it shouldn't be very difficult to eliminate the group, I hope.)

A very cursory examination of Ubuntu documentation leads me to think that I should use Samba, but I'll see as I get further into it.

---

### Post by jonandrews on 2012-05-21
I've written a guide to configure basic file sharing etc between Ubuntu & Windows 7. It was written using older versions of Ubuntu, but I've recently checked it against 12.04, and it is unchanged. Go to [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/) . I hope this helps.

---

### Post by Dave_in_MD on 2012-05-21
> **jonandrews said:**
> I've written a guide to configure basic file sharing etc between Ubuntu & Windows 7. It was written using older versions of Ubuntu, but I've recently checked it against 12.04, and it is unchanged. Go to [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/) . I hope this helps.


Thank you for this, you have been bookmarked. I have 5 Win7 machines and now 2 Ubuntu 12.04, one is a different type of dual booting using BIOS boot priority, on the same net at home, My Ubuntu machine can mount and see the hard drive of the idle 7 drive on the same machine, I haven't checked my granddaughter's Ubuntu machine yet, I have gone no further at this point. Next will be to attempt to get access to the printers which are local to my 7 machine, and local to my wife's 7 machine, we can share the printers from any of the 7 machines but not the XP as it uses IPv4 where the 7s use IPv6.  I still have to keep a XP around as we are a split house at work, classrooms are 7 administration are XP.  If I can get all of this smooth then I will see about connecting to a Win domain. I did a VM for the director of education and he found some interest in the educational SW that is available, and he has a group of i Pads which we connect to the network.

Thanks again

---

### Post by walt11 on 2012-05-22
> **jonandrews said:**
> I've written a guide to configure basic file sharing etc between Ubuntu & Windows 7. It was written using older versions of Ubuntu, but I've recently checked it against 12.04, and it is unchanged. Go to [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/) . I hope this helps.

Thanks from me also. Your guide and the info on Windows Workgroups have got a lot of very helpful information, but it looks like I don't meet the criteria for using them. I don't have an existing network of Windows PCs, but here's what I do have:[INDENT]A (wireless) laptop running Window 7
A (wired) desktop running XP
[/INDENT]If I can get those two networked, then I want to add Ubuntu:[INDENT]12.04 which boots either from an external drive or a flash drive which is normally attached to the same PC that runs XP.
[/INDENT]Is such a setup feasible?
Initially, I need help in just getting the two Windows PCs networked.

---

### Post by Dave_in_MD on 2012-05-22
> **walt11 said:**
> [INDENT]A (wireless) laptop running Window 7
A (wired) desktop running XP
[/INDENT]If I can get those two networked, then I want to add Ubuntu:[INDENT]12.04 which boots either from an external drive or a flash drive which is normally attached to the same PC that runs XP.
[/INDENT]Is such a setup feasible?
Initially, I need help in just getting the two Windows PCs networked.

You can network the 2 but not automatically like you can 2 XP machines or 2 Win7 machines.  It would have to be done with IPv4 as XP does not support IPv6 without add on software.  Disconnect from the outside word, turn your firewall and virus protection off, (some anti virus have their own firewall) share some folders and see what you can see across the connection. Get them working that way, then try reactivating the virus protection one at a time and see if you still have connectivity.  Then again one at a time, bring up a firewall.  It will likely fail at this time.  Check the logs and see if you can see what ports got blocked and open them.  If you cant you will need a packet sniffer like Ethereal, now known as Wire Shark  to capture traffic and see what ports are needed.  Or google as someone should have a list of what ports need to be opened between a win 7 and xp machine.

---

### Post by walt11 on 2012-05-22
Thanks. I appreciate your response. But it sounds like more than I want to (or am able to!) deal with and I'm thinking now of a different approach.

The reason I wanted an XP and Win 7 network was because I thought that was the way to go- to add Ubuntu to an existing network (and that the XP/Win7 part would be easy!). I actually use XP very little now, and would like to get Ubuntu networked with Win 7. The systems I would have to deal with then are:[INDENT]Ubuntu 12.04 running on my wired desktop
Windows 7 running on my wireless laptop
[/INDENT]From just a quick look at Ubuntu documentation, Samba seemed like an approach that would work in both the Linux and Windows worlds, and that configuring things from the Ubuntu side was distinctly better than trying to do much of it from the Windows side. Is that a reasonable way to go about it?

---

### Post by jonandrews on 2012-05-23
In essence, it is a reasonable way to go. All you have to do is to:

Firstly: configure the Win7 machine for networking as follows:
In  'Network & Sharing Centre' click on 'Advanced Sharing Settings'
On the resulting page called 'Change Sharing Options for...etc.' set the following options:
Network Discovery > Turn on
File & Printer sharing > Turn On
Public Folder Sharing > Turn on Sharing
Media Streaming > (Leave off)
File Sharing Connections > Enable sharing for 40 -56 bit...
Password Protected Sharing > Turn off
HomeGroup Connections > Use User accounts & Passwords...etc

Save the changes & reboot (just to be sure)
The Win7 pc will now be visible to a network, along with it's public folders.

Having set up the Win7 pc, now use my guide to configue the Ubuntu pc ( which causes Samba to be installed).

You will then be able to move files between the machines.

---

### Post by Dave_in_MD on 2012-05-23
I am sitting here in front of my Ubuntu machine and one of my 7 machines, the only one awake at the moment.  At this point other than sharing the wire I have done nothing to network them.  Clicking on home folder then  Browse Network I can see my 7 machine and the windows network.  Double clicking the 7 machine I see the shares as well as the hard drive however password is requested.  I have no password set on that machine it does not want the windows network password, It seems that being the sharing is controlled by the Windows workgroup network I can not connect, only see the shares. same result if I drill down into the windows network.  From the Windows machine I can not see the Ubuntu Machine

---

### Post by walt11 on 2012-05-24
> **jonandrews said:**
> In essence, it is a reasonable way to go. All you have to do is to:

Thank you! I really needed the cookbook approach, and I appreciate  it. Setting up the share from the Ubuntu side worked perfectly as per  your guide, and I was able to transfer a file from my Ubuntu PC

I  followed your instructions for configuring the win7 machine, and that  appeared to go well. But on the Ubuntu machine, when I open Network, here's  what I see:

An icon for my printer
An icon for the Ubuntu machine (called EMACHINES-T6520)
An icon for the laptop (called WALT-NOTEBOOK) If I try to open this I get:[INDENT]"Unable to mount location- Failed to retrieve share list from server"
[/INDENT]BUT, there is a 4th icon called "Windows Network"
When I open it, I get another icon, named WORKGROUP.
And,  when I dbl-click that, I again get the first 3 icons that I described  above. And when I try to open WALT-NOTEBOOK I get the same error message  as above. I've tried this several times, and once I got a different  error message:[INDENT]"Could not display 'smb://walt-notebook'-  Error: Failed to retrieve share list from server. Please select another  viewer and try again."
[/INDENT]What do I need to do to make it work?

---

### Post by Morbius1 on 2012-05-24
It looks like a netbios name - to - ip address conversion problem to me. You can verify that by changing your access method from this:
```
nautilus smb://walt-notebook
```To this:
```
nautilus smb://192.168.0.100
```[COLOR=Blue][I]Where 192.168.0.100 is the ip address of "walt-notebook"

[/I][COLOR=Black]If it works by ip address then edit smb.conf as root:
[/COLOR][/COLOR]```
[COLOR=Black]gksu gedit /etc/samba/smb.conf[/COLOR]
```[COLOR=Blue][COLOR=Black]
And add a line to the [global] section - right under the workgroup line is where I'd put it:
[/COLOR][/COLOR]```
[COLOR=Black]name resolve order = bcast host lmhosts wins[/COLOR]
```[COLOR=Blue][COLOR=Black][COLOR=Blue][I]bcast is the only method that woks by default, it's listed last by default, and sometimes "wins" gets in the way which is why I put it last.

[/I][COLOR=Black]Then restart samba:
[/COLOR][/COLOR][/COLOR][/COLOR]```
sudo service nmbd restart
sudo service smbd restart
```Wait a few minutes for the network to settle down and then try to access the shares.

---

### Post by walt11 on 2012-05-24
> **Morbius1 said:**
> It looks like a netbios name - to - ip address conversion problem to me. You can verify that by changing your access method

Thanks for the detailed information. I tried changing the access method, using the ip address supplied by Windows, but got the same error message I reported earlier: "Could not display 'smb://*my ip address*'-  Error: Failed to retrieve  share list from server. Please select another  viewer and try again."

It may be worth mentioning that I've only received this type of error message once before. All the other times, it's simply "Unable to mount location- Failed to retrieve share list from server"

And this also may be significant. Today when I open Network, I'm only getting the icon for "Windows Network" and not the other 3 I was getting yesterday. When I open Windows Network I get WORKGROUP. However, when I dbl-click on that I get the error message directly: "Unable to mount location- Failed to retrieve share list from server", and not the other 3 icons again as before.

---

### Post by Morbius1 on 2012-05-24
A "could not display" almost sounds like you have some packages missing:
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```
And it's also possible that you aren't a member of the fuse group:
```
sudo gpasswd -a your-user-name fuse
```

---

### Post by walt11 on 2012-05-24
> **Morbius1 said:**
> A "could not display" almost sounds like you have some packages missing:
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```And it's also possible that you aren't a member of the fuse group:
```
sudo gpasswd -a your-user-name fuse
```

I found that both gvs-backends and gvs-fuse were already installed, but I did execute the gpasswd command, and rebooted. The windows I'm getting now correspond to the note at the end of jonandrews' guide (and that I was getting last night, but not earlier today) but at the final click, I still get the error message. Here's how it looks:[INDENT]Network window shows the Ubuntu machine, my notebook, and the "Windows Network" entry. I open "Windows Network".

Windows Network shows the one entry WORKGROUP.

WORKGROUP shows printer, Ubuntu machine, and laptop (WALT-NOTEBOOK)
[/INDENT]But when I try to open WALT-NOTEBOOK I still get[INDENT]Unable to mount location
Failed to retrieve share list from server
[/INDENT]As you can see, I understand very little of the workings of this, but could there be a problem on the Windows side? Maybe there is something I failed to set up, which is causing the server there to malfunction. How can I check that out?

---

### Post by Morbius1 on 2012-05-25
** Disable whatever firewall you have set up on the Windows machine and try to access it again.

** If that still doesn&#8217;t get you anywhere then run the following diagnostic command:
```
smbtree
```If you get a listing of all your Linux shares but only a listing of the Windows host name without it's shares then run smbtree this way:
```
smbtree -U morbius
```[I]
[COLOR=Blue]Where morbius is a username on the Windows box. When smbtree asks for a password enter the Window's user's password.[/COLOR][/I]

If you now get a listing of the WIndows shares without any errors being reported run the following command:
```
 nautilus smb://morbius@walt-notebook
```
OR
```
 nautilus smb://morbius@192.168.0.100
```

---

### Post by walt11 on 2012-05-25
> **Morbius1 said:**
> If you now get a listing of the WIndows shares without any errors being reported run the following command:
```
 nautilus smb://morbius@walt-notebook
```OR
```
 nautilus smb://morbius@192.168.0.100
```

Success!

I didn't get the listing, but decided to try the commands, and the one with the ip address worked! In fact, it worked without the username@ preface - which is what you suggested in your first post. It didn't work then (but I've since been added to the fuse group per your instructions).

In any case, I added the line you provided to smb.conf, and it now works from the Network window.

Thank you for sticking with me, and for all your good help. Many thanks also to jonandrews without whose instructions for configuring win7, and his guide, I would not even have got off the ground. Thanks also to the others who responded.

I was thinking of marking this solved, but first I want to change the computer names, and that will make some waves. I may also now try to include my XP machine - maybe.

---

### Post by jonandrews on 2012-05-26
I'm glad you've got it sorted out, walt11. I have also experienced the 'Unable to mount etc' error on occasion, and have always had to resort to rebooting all the machines on the network to resolve it. I will also be trying out the solution from Morbius1, so thanks for that.

---

### Post by jonandrews on 2012-05-26
To Dave_in_MD:  If I understand your last post correctly, my thoughts are as follows
1 - From the Ubuntu pc, by default you are able to see and access shared windows folders. The password request you are getting is from windows, and you need to enter your windows user name & password. If you don't have a windows password, then the password is [leave it blank].

2 - If you have done nothing on the Ubuntu pc to set up sharing, then it it quite right that you will not be able to see it from a windows pc.  To set up sharing, follow my guide on [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/).

I hope I have understood your situation correctly.

---

### Post by welshlion on 2012-05-26
Reading through this thread,I noticed that there was a suggestion that "media streaming" should be "off" in the network set up on Windows 7. I discovered that networking would only work if it is turned "on".
Hope this helps...

---

### Post by jonandrews on 2012-05-26
To Dave_in_MD: I'm sorry - I forgot to say that I have assumed that you configured your Windows 7 network setting in line with my guidelines earlier in this thread. ie:

In 'Network & Sharing Centre' click on 'Advanced Sharing Settings'
On the resulting page called 'Change Sharing Options for...etc.' set the following options:
Network Discovery > Turn on
File & Printer sharing > Turn On
Public Folder Sharing > Turn on Sharing
Media Streaming > (Leave off)
File Sharing Connections > Enable sharing for 40 -56 bit...
Password Protected Sharing > Turn off
HomeGroup Connections > Use User accounts & Passwords...etc

Save the changes & reboot (just to be sure)
The Win7 pc will now be visible to a network, along with it's public folders.

---

### Post by jonandrews on 2012-05-27
> **welshlion said:**
> Reading through this thread,I noticed that there was a suggestion that "media streaming" should be "off" in the network set up on Windows 7. I discovered that networking would only work if it is turned "on".
...
Hi WelshLion- I know that we all experience some odd behaviour by individual systems, but I can assure you that the media streaming setting in Win7 is irrelevant to file sharing. I have 5 Win7 pc's on my network right now with it turned off, all of them sharing between themselves and Ubuntu & Apple pc's.

---

### Post by Dave_in_MD on 2012-05-27
> **jonandrews said:**
> To Dave_in_MD:  If I understand your last post correctly, my thoughts are as follows
1 - From the Ubuntu pc, by default you are able to see and access shared windows folders. The password request you are getting is from windows, and you need to enter your windows user name & password. If you don't have a windows password, then the password is [leave it blank].

2 - If you have done nothing on the Ubuntu pc to set up sharing, then it it quite right that you will not be able to see it from a windows pc.  To set up sharing, follow my guide on [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/).

I hope I have understood your situation correctly.

I was just giving the op an idea as to what he may see, but that if he can not access the shares it just may not be set up completely.  Once I set up a share other than the windows homegroup and set up a share on the Ubuntu box so that it would download the needed package all worked as it should.  I just haven't tried the printer at this time.
Thank You for your efforts.  I passed your web link on to someone else on another thread  as well.

---

### Post by walt11 on 2012-05-29
Got the computer names changed, and added my XP system to the network - which was surprisingly easy, thanks to jonandrews' Windows Workgroups guide. I'm going to mark this thread solved. Thanks again to all for your help.

---

### Post by Ambimom on 2012-06-12
I installed Ubuntu 12.04 on my laptop.  I have Windows 7 on my desktop.  I have been able to share the printer; I can access all the Ubuntu files on my Windows 7 desktop ......but 

When I first set up and installed Ubuntu, it recognized the Windows Workgroup and I could access my Windows files with no problem.  I could share between the two computers in either direction.

The next day when I booted, though Ubuntu recognized the Windows 7 Workgroup  I could not access the files anymore.  

I spent the better part of the day changing all the settings in different ways hoping to fix the problem but nothing worked.

It is driving me crazy.  Is this a bug?  Or am I doing something wrong.

---

### Post by walt11 on 2012-06-12
I probably shouldn't be offering advice, since I've needed so much myself, but-

When I set up the sharing on the Win7 PC, I followed jonandrews' detailed instructions at Post #9. If you haven't already, it may be worthwhile to check that yours conforms to that.

Once I was able to connect to the WORKGROUP (named exactly that), I'm asked for my Windows password twice: once to get access to the Win7 PC, and again to get access to the users directory. Once I've done that, I can access all the files.

---

### Post by Ambimom on 2012-06-12
@Walt11, Thanks so much for your prompt reply.   I tried your suggestion, and changed the Advanced Sharing in Windows 7.  The same thing happened.  I could see my Windows 7 Workgroup listed under the Ubuntu Network but it wouldn't let me access them.  

Then I tried another approach.

I asked Ubuntu to "connect to server" and inserted the ip of my Windows 7 desktop for "Share" service.  The domain was Workgroup, and the passwords and identifiers were my Windows passwords....

Next thing I know I have full access sharing between both computers.  I don't know why 

I guess I have to do this manually every time I want sharing....I sure wish it was automatic....but at least it's working.

Thanks again!

---

### Post by walt11 on 2012-06-12
I never tried the "connect to server" approach, and I'm glad it worked for you. I wonder if the system will retain that connection information, and it will be more automatic next time.

I don't recall if Windows instructs you to reboot after changing the advanced sharing, but it would be a good idea (although, you've probably done that).

---

### Post by sunson565 on 2012-06-30
> **jonandrews said:**
> I've written a guide to configure basic file sharing etc between Ubuntu & Windows 7. It was written using older versions of Ubuntu, but I've recently checked it against 12.04, and it is unchanged. Go to [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/) . I hope this helps.
Thx that was helpful

---

### Post by rmaultz on 2012-06-30
Windows 7 requires  you  to set specific  user permissions  /  Read/ write  for  every  share   and  also  set user name  and  password  for all users  on the  windows  computer 

 i have  dealt with this before easy solution  configure  all windows users with a password  and then   set  read / write permissions in windows  by right clicking  on the folder  or  drive you are sharing  and choose sharing options And then  set the users allowed  to connect to the  shares and  you  will have to log in   on  ubuntu  machine  with one of the admin user account  set up on the windows machine

---

### Post by VidiMan on 2012-08-14
> **walt11 said:**
> I probably shouldn't be offering advice, since I've needed so much myself, but-

When I set up the sharing on the Win7 PC, I followed jonandrews' detailed instructions at Post #9. If you haven't already, it may be worthwhile to check that yours conforms to that.

Once I was able to connect to the WORKGROUP (named exactly that), I'm asked for my Windows password twice: once to get access to the Win7 PC, and again to get access to the users directory. Once I've done that, I can access all the files.
Since you struggled the most I consider your advice more tested. Will try your solution.

---

### Post by chuckrp on 2012-08-16
Here is a new question concerning the same issue. I was able to connect the Win 7 to Mythbuntu computer. It worked perfect the first 2 times. Since I have rebooted the computers they will not talk to each other. The Myth computer still sees the Win 7 computer but will not talk to it. The Win 7 computer does not see the Myth computer. I can not ping it or by typing the address into the run bar. What do you think? Is this something that anyone else has had before?
 

See the messages in "Network Mythbuntu to Windows 7" forum for all the other messages.

---

### Post by jeboza on 2012-09-07
Thx, worked for me and was able to setup my shares with Samba. I bookmarked them after specifying each one by ip address and renaming them to the Windows machine name. 

I still can't use the 'browse network' or see this machine from Windows 7 or from my Mac and a Linux Mint 13 install.

Other than that, I'm glad to be able to move data around again.

Thanks again

---

### Post by Rezliw on 2012-10-27
> **jeboza said:**
> Thx, worked for me and was able to setup my shares with Samba. I bookmarked them after specifying each one by ip address and renaming them to the Windows machine name. 

I still can't use the 'browse network' or see this machine from Windows 7 or from my Mac and a Linux Mint 13 install.

Other than that, I'm glad to be able to move data around again.

Thanks again

Come on!  It shouldn't be this damn hard.   :(

---

### Post by Rezliw on 2012-11-01
OK, finally figured out it works like my Mac OS 10 and the windows network, I signed up for this adventure  :lolflag: and am having hugh highs and lows.  
 
[http://ubuntuforums.org/showthread.php?t=2078772](http://ubuntuforums.org/showthread.php?t=2078772)
 
.
 
:)
.
.

---


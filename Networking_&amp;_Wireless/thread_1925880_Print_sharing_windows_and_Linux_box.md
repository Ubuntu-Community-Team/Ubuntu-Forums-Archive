---
title: "Print sharing windows and Linux box"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by rapattack1 on 2012-02-15
Hi a friend tried to help me last night with print sharing and my two machines. I am not experienced with this and we ran up against an obsticle with the Linux box. He used a program i downloaded called ShowMyPC and was able to do whatever had to be done on windowsxp but my Ubuntu box wasn't so compliant. The printer is plugged into the Windows box and both machines share the internet via a router. The linux box runs Artistx which is a Ubuntu based thing. I am no expert but am pretty good at following instructions as i mainly use linux these days. The path i think i followed to try to set up the print share thing is computer>network servers>windows network>workgroup>[computer name]>print$ then a dialog box pops up and it says 'password required for share print on [computer name]'. username [computer name], domanin:workgroup, password: this feild is blank. under that i can choose from forget password immediately or remember password until you logout or remember forever. Ten there is two buttons 'cancel or 'connect'. i tried all the options and repeatedly put the password in and nothing connected. The dialog box would blink every attempt but no moving forward. So this is where i got up to and would appreciate any advice...thanks :0)

---

### Post by Perkins on 2012-02-21
The username and password parameters will be for a user account on the windows box that has permission to access the share.  If the share is unprotected you can often leave them blank.  If that doesn't work I might be able to help you figure it out, but will need a better description of the problem.

---

### Post by rapattack1 on 2012-02-22
The windows part is done. I had someone do all that. Using showmypc program. Its linux that is the problem not windows. Sorry i don't know what to add as it has been days so my memory has dropped out and i was getting instructed over the net(skype). We hit a bump with ubuntu. Maybe if i follow what i said in the original post and did a desktop capture you can see visually what did not take place/happen/complete

---

### Post by Perkins on 2012-02-22
skype is available for Linux, and it supports screen sharing.  My username is perkinl.  If you can catch me online I'll see what I can do to help if you like.

---

### Post by rapattack1 on 2012-02-22
Oh i didn't know skype did that. I am rapattack55 on it and have added you.Thanks so much as this is a bit baffling

---

### Post by rapattack1 on 2012-02-28
Sorry i forgot to contact you on skype and have been really busy! The update is that i got a parallel port installed and the multifuntion printer(samsung scx-4521f) is using the samsung scx-4200 print driver on the linux box now. Only thing is i can't scan . I have done a fair bit of googling on this but it involves editing using gedit and i am not that good at that. Most of the things i saw were old so wasn't sure they were relevent anyway. So will try and remember to say hey on skype if i see you there :0)

---

### Post by Perkins on 2012-02-29
I saw you go past a couple of times without contacting me and figured you were either too busy or had solved it, so I quit turning it on.  I'll switch it on tomorrow and see if you're around.  Also if my internet connection works decently, the winter storms have been playing hob with it lately.


Most likely the instruction sets you've found are how to tell SANE which set of firmware to use for controlling the scanner.  They are almost certainly still accurate.  The key to using instructions that involve editing config files is to read both the instructions and the files you're changing carefully.  If you can piece together at least some idea of what you're changing it makes it a lot easier to interpolate through any differences in your particular system.


If you post links to the instructions you've found I'll take a look at them and see if they're likely to be anything close to what's needed.

---

### Post by rapattack1 on 2012-02-29
Hi yeah sorry i was probably just distracted and didn't look at skype. If it is down where the tray is i can't see who is online and most people don't seem to use it anymore. Had it for maybe 10 years and people just don't seem to chat anymore. Trying to find the info but my brain is on half right now because of shopping and crappy weather......so looking but will take a while.

Found the thing below while i was looking under the server settings of printing. Not sure if this is something. I checked all the boxes and was able to scan for a printer. The button to proceed which is the OK button at the bottom was never ungreyed so not able to progress. So if this means something i am not sure. Still trying to search for the pages i was looking at that i referred to above but not sure if i will find them.

Found this [http://forum.tinycorelinux.net/index.php?topic=10816.0](http://forum.tinycorelinux.net/index.php?topic=10816.0)


Oh and i think this might be the right one [http://forums.linuxmint.com/viewtopic.php?f=141&t=57503](http://forums.linuxmint.com/viewtopic.php?f=141&t=57503)

---

### Post by Perkins on 2012-02-29
The thumbnail you attached shows the SMB browser, which won't let you click OK because it's got the workgroup and the machine, but not the actual printer.  Furthermore, the machine it shows is listed as being of type "Samba, Ubuntu", so I'm guessing that it's actually the machine who's screen I'm looking at, and not the Windows machine with the printer.

If you go into the printer's sharing properties on the windows machine it should list under what name the printer is shared, and if you go into the My Computer properties there should be a tab that lists the computer name and the workgroup.  You can manually punch those into the location field for the printer sharing setup, which is the box in that screenshot with the smb:// to the left of it.  Instructions for how to format it are in the line below the box.

The first link you posted appears to have instructions for how to install the scanner drivers.  They may or may not support scanning over the network.  I know the HP linux drivers do, but I don't know about Samsung.  Unless there is something in the documentation that says one way or another I guess you'll just have to try it and see.

---

### Post by rapattack1 on 2012-03-01
Sorry that all went over my head. I now do not remember anything that happened on the windows machine. I would have to read what i said in the first post and even then i didn't understand it when the guy did it. OK so in doing all of this print share thing i may not acheive scanning via linux? If thats the case then i don't need to worry because i have the printing thing happening. That page did say there was a scanner driver but the beginnings of it is what i don't understand. Wish i understood more but with my medical condition i have come a long way so far....going to take too long for me to ....i dunno i am so tired i can't seem to get the words out....all i know is i can't proceed ;)

---

### Post by Perkins on 2012-03-02
In more simple terms, from the screenshot you sent, your linux machine sees only itself on the network.  The linux machine has no printer, ergo there are no printers available for you to connect to.


Most likely, the Windows machine doesn't actually have file and print sharing enabled, and so does not show up in your list.

If you go into the printer settings page on the windows machine (what it's called depends on the version of Windows, but it's usually available in the start menu) and right-click on the printer and choose sharing, it should tell you if the printer is actually shared or not, and what it is called on the network.

Once you have the name of the printer right-click on My Computer and choose properties and look in the computer name tab and get the name.  Then you can manually punch in //computer/printer into the share location in the printer setup on the linux machine and it should theoretically work as long as the share is accessible.

---

### Post by rapattack1 on 2012-03-02
OK i only half follow what your saying about the linux machine. I can print because i have the printer connected via a parallel cable now but not as a network printer.

Yes the windows machine is taken care of. The guy that did it for me is an IT guy and that is his area of expertise. We did the windows(XP) part first and then we went over to the linux box and tried to do whatever it was we did. When things are not so busy i will do some captures of whatever as its hard to concentrate with too much happening right now.

---

### Post by rapattack1 on 2012-03-03
Hi is the thing that you wanted me to post? Hope its the right thing :0) sorry saw u online earlier but i was getting ready to go to  major event :0)

---

### Post by Morbius1 on 2012-03-03
> Yes the windows machine is taken care of.No it is not. Based on the screenshot you posted on panel #8 it does not see the Windows machine "CARMEN-9C4BAE97".  

You either need to follow the instructions that Perkins posted in Panel #11 or if you have already done that then you need to temporarily disable the firewall on WinXP and Ubuntu ( if you did anything to it in Ubuntu ) to see if the firewalls are getting in the way.

Why not run the following command to see how your system sees the network. It will produce error messages if it sees something wrong:
```
smbtree
```

---

### Post by rapattack1 on 2012-03-03
No i meant the windows machine is configured....whatever i don't know the wording. That screen shot you mentioned is from the linux box not the windows one! As i said linux is not seeing the windows whatever. I said that before.
Yes i don't understand the instructions so was waiting for more clarification....this is not something i have ever done or seen done.
Ami running that command on linux or windows?

---

### Post by Morbius1 on 2012-03-03
smbtree is run from linux

---

### Post by rapattack1 on 2012-03-03
```
 smbtree
Enter carla's password: 
WORKGROUP
	\\CARLA-DESKTOP  		carla-desktop server (Samba, Ubuntu)
		\\CARLA-DESKTOP\IPC$           	IPC Service (carla-desktop server (Samba, Ubuntu))
		\\CARLA-DESKTOP\print$         	Printer Drivers
MSHOME

```

---

### Post by Morbius1 on 2012-03-03
Your Linux box cannot see the Windows box.

* Turn off the firewall on the Windows box, run smbtree again, and see if smbtree lists all of the shares on that box.

---

### Post by rapattack1 on 2012-03-03
```
smbtree
Enter carla's password: 
WORKGROUP
	\\CARLA-DESKTOP  		carla-desktop server (Samba, Ubuntu)
		\\CARLA-DESKTOP\IPC$           	IPC Service (carla-desktop server (Samba, Ubuntu))
		\\CARLA-DESKTOP\print$         	Printer Drivers
MSHOME
carla@carla-desktop:~$ smbtree
Enter carla's password: 
WORKGROUP
	\\CARLA-DESKTOP  		carla-desktop server (Samba, Ubuntu)
		\\CARLA-DESKTOP\IPC$           	IPC Service (carla-desktop server (Samba, Ubuntu))
		\\CARLA-DESKTOP\print$         	Printer Drivers

```

---

### Post by rapattack1 on 2012-03-03
Something just occurred to me....i am very tired so bare with me. Now this was originally done with the usb connection. Now that is not the case. Now the printer is connected via usb to windows and parallel to linux box....so this would not be working at present. I am too tired to proceed tonight so can we give it a couple of days and i will come back to it

---

### Post by Morbius1 on 2012-03-03
The thing that makes this interesting is that smbtree throws you no errors. If it was the usual problem with netbios name resolution - something that can be fixed in Linux - it would produce a typical error message but in this case you get nothing.

If the Windows firewall is truly off then off the top of my head:

* The Windows box is not on the network.
* The Windows box is on another subnet and samba can't browse by name to another subnet - normally.

What happens when you run the folowing command:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Windows box.*[/COLOR]

It won't show the printer but it should show Windows' administrative shares if nothing else.

---

### Post by rapattack1 on 2012-03-03
Hi thanks will get back to this in a couple of days....sorry was at a major event that went for hours and i did say something that might be the cause above....mind blowing headache is turning into a migraine...thanks gotta go

---

### Post by Perkins on 2012-03-03
That second thumbnail is one of the places I was hoping you'd look at.  If you see the line there that says, "Full Computer Name:" The Carmen-9C4BAE97 part is the name of the Windows machine.  When you get everything set so that the two machines can see each other, you'll see \\Carmen-9C4BAE97 show up in the output from smbtree on the linux machine.


If connecting to the Linux machine with a parallel cable is a satisfactory setup physically, you may be happier just leaving it that way since A) you won't have to have the Windows machine turned on to print things and B) the scanner is almost guaranteed to work via parallel cable whereas I'd estimate about a 50% chance of it working via network share.


Post back when you have time to work on it more.

---

### Post by rapattack1 on 2012-03-04
OK its possible i didn't turn the internet on on the windows machine and the printer so thats maybe why things stuffed up....not sure. OK tried that command again with both on. First time with firewall on and 2nd time without. That looks like it worked :0)
```
carla@carla-desktop:~$ smbtree
Enter carla's password: 
WORKGROUP
	\\CARLA-DESKTOP  		carla-desktop server (Samba, Ubuntu)
		\\CARLA-DESKTOP\IPC$           	IPC Service (carla-desktop server (Samba, Ubuntu))
		\\CARLA-DESKTOP\print$         	Printer Drivers
carla@carla-desktop:~$ smbtree
Enter carla's password: 
WORKGROUP
	\\CARLA-DESKTOP  		carla-desktop server (Samba, Ubuntu)
		\\CARLA-DESKTOP\IPC$           	IPC Service (carla-desktop server (Samba, Ubuntu))
		\\CARLA-DESKTOP\print$         	Printer Drivers
MSHOME
	\\CARMEN-9C4BAE97		XP
		\\CARMEN-9C4BAE97\Printer        	SmarThru PC Fax
		\\CARMEN-9C4BAE97\SamsungS       	Samsung SCX-4x21 Series
		\\CARMEN-9C4BAE97\C$             	Default share
		\\CARMEN-9C4BAE97\ADMIN$         	Remote Admin
		\\CARMEN-9C4BAE97\Printer5       	Microsoft Office Document Image Writer
		\\CARMEN-9C4BAE97\Printer4       	Microsoft XPS Document Writer
		\\CARMEN-9C4BAE97\Printer3       	Panasonic KX-P7100
		\\CARMEN-9C4BAE97\Printer6       	Brother HL-1430 series
		\\CARMEN-9C4BAE97\SharedDocs     	
		\\CARMEN-9C4BAE97\print$         	Printer Drivers
		\\CARMEN-9C4BAE97\IPC$           	Remote IPC


```

Oh how do i find out the ip address of the windows box? Sorry been a long time since i knew how to do that.


Yes it prints fine using the parallel cable but i can't scan. Will i be able to scan without disabling this firewall? 
Thanks guys i have my brain half on today but still worn out so bare with me :0)

---

### Post by Morbius1 on 2012-03-04
Make sure the firewall if off on WinXP, then in a terminal on Ubuntu type:
```
system-config-printer
```Then click on the "+" sign or Add, then select "Network Printer" > "Windows Printer via SAMBA"

In the "smb://" dialog box enter:
```
CARMEN-9C4BAE97/SamsungS
```Then click "Verify" to see if it connects.

---

### Post by rapattack1 on 2012-03-04
Yep it worked. I did a test print with the firewall off then i turned it on and i did another test print. I tried to do a scan at the same time using xsane and a couple of other scanning apps here on linux but no luck

---

### Post by Perkins on 2012-03-04
If the scanner is going to work via network share you'll almost certainly need to install the drivers you found.  And even then it probably won't work unless Samsung is using some magic to make it work.  The driver is quite likely to let you use the scanner via USB, Parallel, or both.

---

### Post by rapattack1 on 2012-03-04
What do you mean to install the drivers? The device is working via windows and the usb connection right now....drivers installed ages ago....sorry not following.

---

### Post by Perkins on 2012-03-05
If the people who wrote the Linux drivers are at all competent, installing them on the Linux machine, as detailed in that set of instructions you found, should allow you to use the scanner via USB or parallel port.  You might or might not be able to use the scanner via the network share.

---

### Post by rapattack1 on 2012-03-05
Oh ok....i don't know i can't understand those instruction for installing linux drivers so i am stuck there. The first part i can't understand so didn't get started :0(

---

### Post by Perkins on 2012-03-06
[http://forums.linuxmint.com/viewtopic.php?f=141&t=57503](http://forums.linuxmint.com/viewtopic.php?f=141&t=57503)

For the scanner you'll need to follow step 1 and step 3 and see if it works.  However it is quite likely that you'll need the scanner connected directly to the linux machine for the scanner to work.  I would be very surprised if it works via network share.

If you need help figuring out what those two steps are asking you to do, let me know and I can explain them in more detail.

---

### Post by rapattack1 on 2012-03-06
Ah ok yeah directly using the parallel connection would be better> ok yeah i did find it hard to understand those instructions right from the beginning so any help would be greatly appreciated...:0)

---

### Post by Perkins on 2012-03-08
Open System->Administration->Software Sources.

Go to the "Other Software" tab.

Click the add button and put in:  deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

That is the repository that has the drivers for your printer.

In a terminal type ```
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
```

That prevents someone else from impersonating the repository that holds the drivers.

run:
```
sudo apt-get update
sudo apt-get install samsungmfp-scanner
```

This installs the official Samsung driver, which should be able to run the scanner.

Fire up xsane and see if it detects your scanner.  If it doesn't with the parallel cable, try with the USB cable and we'll go from there.

---

### Post by rapattack1 on 2012-03-08
Well everything seemed to go ok but xsane didn't see the scanner....with the parallel cable...will have to check with the usb cable later. Hope i remember...thanks

---

### Post by Perkins on 2012-03-09
Check it with the USB.  Making it work through the parallel cable would probably require us to dig into the SANE settings and specifically tell it to check the parallel port for a scanner.  Which we can do if you think it's worth the effort.

---

### Post by rapattack1 on 2012-03-10
Hi no xsane didn't see the scanner this time round with the usb cable. All the system did is see the printer straight away and install the printer .

---

### Post by Perkins on 2012-03-10
hmmm...

Try:
```

sudo adduser carla lp
sudo adduser carla lpadmin

```

Then reboot and see if it works any better.  If not then we'll have to figure out what the permissions are on the scanner device or what else is broken.

---

### Post by rapattack1 on 2012-03-11
```
$ sudo adduser carla lp
[sudo] password for carla: 
Adding user `carla' to group `lp' ...
Adding user carla to group lp
Done.
carla@carla-desktop:~$ sudo adduser carla lpadmin
The user `carla' is already a member of `lpadmin'.

```

Rebooted and xsane still doesn't see it

---

### Post by Perkins on 2012-03-13
Well, it's supposed to work...

The next thing to try is to search for xsane and the model of your printer and see if there's anyone who knows what might be doing this...  Because it's supposed to work.

---

### Post by rapattack1 on 2012-03-13
I googled and found a few links but have no time to look until later [https://www.google.com/search?client=ubuntu&channel=fs&q=xsane+samsung+scx-4521f&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=xsane+samsung+scx-4521f&ie=utf-8&oe=utf-8)

---

### Post by rapattack1 on 2012-06-27
I gave up and gave the printer/scanner away but if anyone has some insights into mfc's and printer/scanners then i would like it :0)

---

### Post by Perkins on 2012-06-27
It's pretty much the same on Linux as it is on Windows.  The major difference being that Linux drivers are small enough that most desktop distros just include everything available by default.  (Unfortunately, I have noticed Ubuntu not keeping up in that regard in the last couple of years.)

Unfortunately, not all manufacturers can be bothered to provide drivers, and not all models of printer are common enough for someone to have gone to the effort to reverse-engineer them.  Generally speaking, HP, Epson, Canon, and Brother either just work, or have easy-to-find drivers.  With other manufacturers, check the hardware databases before you buy since there tends to be a lot of variation, sometimes even from model to model.

As for what happened here, the drivers we were trying to install were meant for Debian.  There are some structural differences.  Most of the time they're compatible, but occasionally a wire gets crossed and they don't work quite right.  The other possibility is that the drivers are relatively new, and may not be quite complete.  Sometimes there are a few different versions of the hardware that all have the same model number painted on the outside.

---

### Post by rapattack1 on 2012-06-28
Oh thanks for that info. Luckily i scored a laser printer and separate scanner and they are working well with both Ubuntu and windows :0)

---

### Post by critin on 2012-06-28
> **rapattack1 said:**
> Oh thanks for that info. Luckily i scored a laser printer and separate scanner and they are working well with both Ubuntu and windows :0)

rapattack1,

What brand is that, if you don't mind saying?

---

### Post by rapattack1 on 2012-06-29
The laser printer is a Canon LBP3000 and the scanner is a Canon canoscan LiDE50

---

### Post by critin on 2012-07-01
Thank you!

---

### Post by rapattack1 on 2013-01-04
Seems like this might have been a version issue even though i gave up and got rid of the printer in question. I got another laser printer and tried doing the same with that one and still no go. So then i upgraded to Ubuntu 12.04 and now the printer works directly. I don't have to do the share thing :0) Thanks

---


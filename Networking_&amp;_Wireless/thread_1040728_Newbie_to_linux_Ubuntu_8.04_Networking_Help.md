---
title: "Newbie to linux Ubuntu 8.04 Networking Help"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by stSpringer2003 on 2009-01-15
Hi All,

I am new to linux and Ubuntu 8.04

SETUP:
PC1 Windows XP Pro
PC2 Windows Home

PC1 connects to the internet a-ok
PC2 I installed Unbuntu 8.04 and can dual boot to Windows or Ubuntu I can surf the internet,no problems very smooth.  

I have roadrunner as my ISP with a Broadband connection and an SMC Barricade router wireless and hard wire.

I can browse my lan and internet with PC2 booted into windows.

if I boot into Ubuntu 8.04 on PC2 I can go on the internet but can't see my PC1 box. WORKGROUP same on PC1 and PC2

PC1 name is IntelPC and Shared Name is WinXPPro 
"whole C drive is my share"


MY JOURNEY:
I installed Ubuntu 8.04 from a downloaded ISO on PC2 box.
All went well and I can now dual boot to either Ubuntu or Win XP
I also downloaded all the latest updates for Ubuntu approx 237 of them.

I have never had any issues getting on the internet with Ubuntu of any "flavor", and I can ping both my router ip 192.168.2.1 and the PC1 box IP 192.168.2.29

Problem:
What I can't do is browse my lan PC1 from ubuntu.

I did do my research on this matter and found that there is no clear answer on what I must do to fix this issue. It seems there are so many "flavors" of linux that is it very difficult.

I found a youtube video on Ubuntu 6.10 showing how to browse a lan and I even started from scratch and installed Ubuntu 6.10.

Well what the video showed and what should happen didn't happen on my install. It mentioned in one procedure I would be promped to install **_SMB and NFS _** well that never happened. I was prompted to install them but it never did install them and it kept prompting me over and over but never installed them.

This is what I have been experiencing all along with Ubuntu. It seems like all the suggestions I have found do not work or I get error codes.

I taught myself programming in Visual Basic 6.0 Professional, doa,oop the whole 9 yards, huge learning curve, so I do have patience and I found tons of help on the web for Visual Basic code that "DID WORK".

I'm sure my problem has a simple fix but I can't find the fix.

I am sure there is someone out there that can walk me through this useing Ubuntu 8.04, I've also tried Fedora 10 with no luck.

Should this issue be this difficult? Is browsing my windows box supposed to work right out of the box just like connecting to the internet does?

Please advise.

Thanks for any help

---

### Post by superprash2003 on 2009-01-16
well there have been a few samba nautilus bugs around.. so a current workaround is accessing via ip.. and using nautilus manually.. this should help you [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)
if you dont see the shares the first time, keep refreshing by pressing F5

---

### Post by stSpringer2003 on 2009-01-16
> **superprash2003 said:**
> well there have been a few samba nautilus bugs around.. so a current workaround is accessing via ip.. and using nautilus manually.. this should help you [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)
if you dont see the shares the first time, keep refreshing by pressing F5

It worked! Thanks tons. But here is another example of what I'm talking about.

The instructions said:
Step 1 : Go to Places->Computer
A-OK

Step 2 : The nautilus window should now pop up.
**_"File Browser came up" Is that Nautilus?_**

Step 3 : Now under "Go to" type smb://x.x.x.x where x.x.x.x is the ip address or the machine name of the windows machine which contains the shared folders and hit ENTER.As said earlier you can find that information by typing ipconfig in the command 
prompt of windows machine(eg 192.168.1.3)

There is no "Go To"

I wound up guessing by clicking on "connect to server" and I selected "Windows Share" and punched in my windows box IP 192.168.2.29 and that did it.

Thanks Again

---


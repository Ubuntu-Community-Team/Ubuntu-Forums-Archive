---
title: "Windows network"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Hagbard_C on 2010-10-21
[IMG]http://img210.imageshack.us/img210/5026/screenshotkp.png[/IMG]

hi, where can i find this password, it is neither my password for my windows pc nor my ubuntu password. i just cant connect to my windows computers, i dont know how, it allways wants some password and i just dont know which one.

thanks for your help. hagbard

---

### Post by luvshines on 2010-10-21
Did you try the Windows username and password ??

---

### Post by pietbuntu on 2010-10-21
What version of windows are you running on the PC you want to connect to?

I think it's a sharing issue on the windows.

---

### Post by Hagbard_C on 2010-10-21
im running windows 7, you may be right, i havnt changed any share settings on the computer i want to connect to other than sharing it in a home group and sharing all drives, but ive never found anything like "remote desktop". i also dont know where to find my domain.

ive tried the windows username and password, dosnt work.

---

### Post by luvshines on 2010-10-21
> **Hagbard_C said:**
> 
ive tried the windows username and password, dosnt work.

Ok, if GUI is not working just try the terminal (we may get some relevant error logs):
```

## List the shares
smbclient -L <windows-ip> -U<windows-user>%<user-passwd>

## Access the shares
smbclient //<windows-ip>/<share-name> U<windows-user>%<user-passwd>

```

---

### Post by Hagbard_C on 2010-10-21
sorry, i dont get it. for 1 i don't use a password for my windows machine, my ip is 192.168.2.101 and the username is just Aussie, would the command sound like this:

smbclient -L 192.168.2.101 -U Aussie

because that takes me nowhere (aussie: Not enough '\' characters in service
)

---

### Post by luvshines on 2010-10-21
> **Hagbard_C said:**
> sorry, i dont get it. for 1 i don't use a password for my windows machine, my ip is 192.168.2.101 and the username is just Aussie, would the command sound like this:

smbclient -L 192.168.2.101 -U Aussie

because that takes me nowhere (aussie: Not enough '\' characters in service
)

When you press ENTER with this command, does it asks for a password ??
If it asks for one, just press ENTER again

Or simply type the command without password ```
smbclient -L 192.168.2.101 -U Aussie%
```

---

### Post by Hagbard_C on 2010-10-21
ok this time (i thought i had to do it under the sudo su thingy) it wrote:

Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.2.101 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

the other computer i want to connect to is up and running, logged on, but i havnt done anything for sharing with ubuntu or something like that. should i?

---

### Post by Hagbard_C on 2010-10-21
aussie-ubuntu@aussie-ubuntu:~$ smbclient //192.168.2.101/aussie-pc-ii -U Aussie% 
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

---

### Post by luvshines on 2010-10-21
Oh ok!!
I have seen this error before but couldn't find a solution :(
We had some discussion here:
[http://ubuntuforums.org/showthread.php?t=1597706&page=2](http://ubuntuforums.org/showthread.php?t=1597706&page=2)

See if Comment #14 works for you :-
1. Open nautilus
2. Press ctrl+l, then type smb://<windows-ip>. Press ENTER
3. Then provide username and empty password when it prompts for one

---

### Post by Hagbard_C on 2010-10-21
thats what i have been trying to do from the beginning, the same window opens that i have posted in my picture! it just does nothing, the window disappears and then opens up again.

---

### Post by luvshines on 2010-10-23
Hi

Any success on this one ??

I too setup a Win7 VM since I didn't have one, to check what all options are there which makes sharing so tough

After lot of juggling and torturing my Win 7 machine I am finally able to get Guest sharing working and Admin sharing too but with password(since my admin is password protected)

I will try to recollect what all I did to get it working, but in the meantime just one question for you
**Did you turn off 'password protected sharing' in networki-and-sharing -> advanced sharing options**

---

### Post by Hagbard_C on 2010-10-24
hi im assuming with VM you mean virtual machine? i have 2 pcs, both running and connected to one lan hub which also connects to the internet, i have both pcs on, the w7 one logged on as administrator.

you were asking if i have password disabled, do you mean on the linux or on the w7 pc?

infact i do have linux and w7 installed side by side on the pc i refer to as the linux pc, but im not trying to acces the windows part of the linux pc, im trying to connect to a networked w7 pc.

---

### Post by Hagbard_C on 2010-10-24
"Did you turn off 'password protected sharing' in networki-and-sharing -> advanced sharing options"

following setings are applied in control panel > network and sharing center > advanced sharing setings:
turn on network discovery
turn on file and printer sharing
turn on sharing, so anyone with network access can read and wrtie files in the public folders

in addition to that i have manually shared all drives etc.

ive basically done everything i can think of, i don't think the problem lies with the w7 pc, unless of course its a password issue.
i have tried applying a password to my w7 account and using this password in the linux network (the foto i posted) this also has no effect. (window closes and just opens again)

---

### Post by luvshines on 2010-10-24
Just below the options you have mentioned, there are a couple of more options, see screen-shot.

That has option of turning off password protected sharing

---

### Post by Hagbard_C on 2010-10-24
ok, wasnt able to scroll down because of screensetup, changed it now. the next setings i hav now changed to:

use 128bit encr.
turn off password etc.
use user account etc.

---

### Post by Hagbard_C on 2010-10-24
still no luck (with the graphic interface) ill try the command lines tomorrow.

thanks so far!

---

### Post by luvshines on 2010-10-24
I also noticed that I had to add permissions for 'Everyone' in my windows share to access shares from passwordless administrator.
I added everyone permissions both to 'Sharing' and 'Security' tab in the shared folder on windows

---

### Post by Fahd0o0 on 2010-10-25
The problem of password begin installation Windows Live Messenger 2011

When it is removed the problem disappear

---

### Post by Hagbard_C on 2010-10-25
> **Fahd0o0 said:**
> The problem of password begin installation Windows Live Messenger 2011

When it is removed the problem disappear

how could Windows Live Messenger 2011 possibly have anything to do with it?

---

### Post by luvshines on 2010-10-25
> **Hagbard_C said:**
> how could Windows Live Messenger 2011 possibly have anything to do with it?

Actually, there are bugs related to Windows Live Messenger and Samba
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/458637)
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

---

### Post by Fahd0o0 on 2010-10-25
> **Hagbard_C said:**
> how could Windows Live Messenger 2011 possibly have anything to do with it?

I do not know, but I'm sure the reason is that Windows Live Messenger 2011

The problem starts when you installed

And disappear when you remove it

Does not have a problem between Windows and Windows

But the problem with Linux

The problem is resolved in Samba wait for patching of ubuntu

---

### Post by Hagbard_C on 2010-10-27
you are correct, im one step further now. i can now see the shared drives on my windows pc!!!

the problem is that i am only able to connect to the drive called "Users" all other drives are listed twice, once just as C, D, J and L, and once as C$, D$, J$ and L$, in adition there is also an Admin$. i assume the dollar sign means i need a password, and this is the point at which the same old problem arrises, i do not know which password is neaded. ive tried my linux and windows passwords, nothing works!

---

### Post by luvshines on 2010-10-27
> **Hagbard_C said:**
> you are correct, im one step further now. i can now see the shared drives on my windows pc!!!

the problem is that i am only able to connect to the drive called "Users" all other drives are listed twice, once just as C, D, J and L, and once as C$, D$, J$ and L$, in adition there is also an Admin$. i assume the dollar sign means i need a password, and this is the point at which the same old problem arrises, i do not know which password is neaded. ive tried my linux and windows passwords, nothing works!

I had this issue too when I was testing on the VM's.
I found that I had to add 'Everyone' in the Security(right_click+properties) on Win7 machine. The permissions of Everyone can be controlled by you. The sharing also has to include 'Everyone'
This link also points to the same observation:
[http://social.answers.microsoft.com/Forums/en-US/w7security/thread/23369f35-bc45-4147-9c3e-74a47d530757](http://social.answers.microsoft.com/Forums/en-US/w7security/thread/23369f35-bc45-4147-9c3e-74a47d530757)

---

### Post by Hagbard_C on 2010-10-27
thanks i think ill leave it at that. the public profile is all i need, i just want to sent files back and forth without usb stick.
thanks for all you time and help!!!
you guys are great.

i would really appreciate it if you could send me an email when samba is patched to let it connect to windows although windows live mail is installed, because thats what i usually use!
thanks again.
[email]felix.s@hotmail.de[/email]

---

### Post by luvshines on 2010-10-28
> **Hagbard_C said:**
> thanks i think ill leave it at that. the public profile is all i need, i just want to sent files back and forth without usb stick.
thanks for all you time and help!!!
you guys are great.

i would really appreciate it if you could send me an email when samba is patched to let it connect to windows although windows live mail is installed, because thats what i usually use!
thanks again.
[email]felix.s@hotmail.de[/email]

Sure, but you can still try adding 'everyone' to security and share it with ease :D

For the patch, I think Samba has already been patched but Ubuntu is using the earlier version, but I am not sure

PS: Is that a mail id from Germany ?? If it is, then dude you are in the vicinity of Samba guru, Volker Lendecke . Catch hold of him somewhere, someday and get your stuff resolved/patched :mrgreen:

---


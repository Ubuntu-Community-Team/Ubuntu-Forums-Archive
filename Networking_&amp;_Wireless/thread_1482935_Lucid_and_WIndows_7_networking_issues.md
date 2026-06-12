---
title: "Lucid and WIndows 7 networking issues"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by ShizzlePDX503 on 2010-05-14
So I have two machines on a home network; one machine has Windows 7 and the other has Ubuntu 10.04. When I share a file folder or drive on the Linux machine Windows 7 sees it just fine and I am able to view, copy, edit files and whatnot.

When I share a folder or drive on my Windows 7 machine linux isn't able to view the contents and instead asks for a username, domain, and password. I enter in the information but it keeps asking for the same information.

For the username it defaults to my linux username and for the domain it defaults to WORKGROUP, and the password field is blank. I change the username to the Windows 7 username that I want to use and the domain to HomeGroup (default domain for win7). I know that I have Samba installed on the linux machine. 

Is there something that I am missing? I would much appreciate any information or help that will solve my problem.

---

### Post by parn on 2010-05-14
Have the same issue - nautilus keeps asking me for my credentials but it use to be working in karmic.

I do not have a solution but I use a workaround and mount the windows share from cli

sudo apt-get install smbfs

sudo mount -t cifs //<win7-IP>/folder /my-mount-folder -o rw -o username=user

---

### Post by ShizzlePDX503 on 2010-05-14
great I will give that a try, thanks!

---

### Post by ShizzlePDX503 on 2010-05-14
works great, will I have to do this every time I reboot and how do I unmount it?

---

### Post by parn on 2010-05-14
to unmount - just type:
sudo umount /mount-folder

Well that is the command I type every time I connect to my windows share. If you want to mount the share folder automatically, you will have to add an entry to /etc/fstab

sudo vi /etc/fstab (or any text editor)

Add the line at the end of the file:
//Server-IP/Share /mount-folder cifs _netdev,username=win-user,password=win-password 0 0

Once you have added this line, you can simply type:
    sudo mount /mount-folder
to mount the windows shared folders. The shared folder will also be automatically mounted when you login to your desktop. If you have more than 1 user account and want to limit the auto mounting, you can use the following:

//Server-IP/Share /mount-folder cifs _netdev,username=win-user,password=win-password,uid=linux-user-id,gid=group-id 0 0

---

### Post by ShizzlePDX503 on 2010-05-14
thanks! I found on the internet about having to do the fstab and it sounded kind of confusing to me so thanks for explaining it here.

---

### Post by guy-rouillier on 2010-06-02
I see that you have Win 7 reading and writing files on Ubuntu and I'd like to ask about your samba.conf settings.  I have an XP Pro desktop and a Win 7 Home Premium laptop.  XP Pro is working perfectly with the Samba share on 10.4.  However, I just can't get Win 7 to connect.  I keep getting access denied.  Actually, I found one setting in smb.conf that does allow Win 7 to  connect: 

protocol = LANMAN2

 But this causes more issues  than it solves.  With that set, *both* my XP and Win7 boxes behave very  strangely (and wrongly), e.g., with the following 3 files on the Ubuntu  box:

 ActivePerl-5.10.1.1007-MSWin32-x86-291969.msi
ActivePython-2.6.5.12-win32-x86.msi
ActiveTcl8.6.0.0b2.291226-win32-ix86-threaded.exe

 from  either Win box, typing "a" or "A" and hitting the tab key just produces  a beep.  Typing "dir A*"  lists one file and then "file not found".  So,  using that protocol is not an option.

 Here are the relevant  options I have in smb.conf:

 client lanman auth = yes
client  ntlmv2 auth = yes
lanman auth = yes
ntlm auth = yes

 To get  my XP box to work, only the second one is required (using  LmCompatibilityLevel 2).  On the Win7 box, I've tried  LmCompatibilityLevel 1 and 2  with no difference in outcome.

 I'd appreciate any other ideas.   My frustration level is boiling over.  Ubuntu is 10.4 x86 with Samba  3.4.7.  Thanks.

---

### Post by ShizzlePDX503 on 2010-06-02
This is what my /etc/samba/smb.conf is [http://pastebin.com/te5cA8aF](http://pastebin.com/te5cA8aF)

---

### Post by ShizzlePDX503 on 2010-06-02
I have samba 3.4.7 installed as well, I am not sure if this matters or not but do you have the smbfs package installed? I was having problems similar to the ones you are having until I installed that package.

---

### Post by guy-rouillier on 2010-06-03
Unfortunately, yes, smbfs is installed.  I don't have it configured, though I wouldn't think I would have to.  I'm not attempting to mount anything on Ubuntu to my Win boxes.  I set up this Ubuntu box as a file server.

Here are the errors that Samba is logging for my Win7 laptop - not very helpful:

[2010/06/03 03:03:46,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/06/03 03:03:58,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/06/03 03:03:58,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

I looked at the sample, and nothing jumps out at me.  I tried small things like setting domain logons = yes.  That didn't help.  Interestingly, I commented out *all* the auth and client auth statements, and that didn't make any difference; XP could still get, Win7 still couldn't.

Actually, one thing I do see different is that I'm attempting to use a share outside my home directory.  The sample doesn't have one of those.  Here is my entire smb.conf after running it through testparm:

```

[global]
        workgroup = HOME
        server string = %h server (Samba, Ubuntu)
        interfaces = 127.0.0.0/8, eth0
        bind interfaces only = Yes
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = No
        dns proxy = No
        usershare max shares = 0
        panic action = /usr/share/samba/panic-action %d
        valid users = %S

[data]
        comment = Samba server's /data directory
        path = /data
        valid users = guyr
        read only = No
        locking = No

```Appreciate if anything jumps out at you that might help.  Thanks.

---

### Post by ShizzlePDX503 on 2010-06-03
what happens if you change the protocol from LANMAN2 to NT1?

---

### Post by ShizzlePDX503 on 2010-06-03
have you read this? [https://help.ubuntu.com/community/SettingUpSamba#Windows Clients (XP,Server,Vista, Win7)](https://help.ubuntu.com/community/SettingUpSamba#Windows Clients (XP,Server,Vista, Win7))

---

### Post by _Mark_ on 2010-06-03
Why not in Win 7 turn off the password protected sharing, that's what I did and lucid can connect just fine

Not in front of win 7 at the moment but it is in the Advanced sharing settings for whatever network profile you are running, at the bottom check Turn off password protected sharing.

Of course the caveat to this is only do it if security is not an issue

---

### Post by guy-rouillier on 2010-06-06
> **ShizzlePDX503 said:**
> what happens if you change the protocol from LANMAN2 to NT1?

Same result as if not specifying any protocol at all.  The only protocol that allows Win7 to access the share is LANMAN2.

Thanks for your ideas.  Sorry for not responding more promptly.  I've been checking every day but failed to see that this thread rolled over onto page 2 :(.

---

### Post by guy-rouillier on 2010-06-06
> **ShizzlePDX503 said:**
> have you read this? [https://help.ubuntu.com/community/SettingUpSamba#Windows Clients (XP,Server,Vista, Win7)]("https://help.ubuntu.com/community/SettingUpSamba#Windows%20Clients%20%28XP,Server,Vista,%20Win7%29")

Yes.  Not really applicable, unfortunately.  I have browse = no.  I'm very comfortable with command line tools, so I'm just using 

net use n: \\nas\data mypassword /user:guyr

Thanks.

---

### Post by guy-rouillier on 2010-06-06
> **_Mark_ said:**
> Why not in Win 7 turn off the password protected sharing, that's what I did and lucid can connect just fine

Not in front of win 7 at the moment but it is in the Advanced sharing settings for whatever network profile you are running, at the bottom check Turn off password protected sharing.

Of course the caveat to this is only do it if security is not an issue

I think this only applies if Win7 is the file server, right?  In my case, Win7 is a client, and Ubuntu 10.4 is the server.  I suppose I could try share level security just to see if it works.  But rather than do that, I'd probably just stick with user level security and use sftp to get to the files from Win7.

Update: I tried switching smb.conf to use security = share, and it works from both XP and Win7.  Since this is a home network and I'm behind my router's firewall, I can probably get by with share level security.  

Thanks.

---

### Post by guy-rouillier on 2010-06-08
For those who may find this thread via search:

With the help of the Samba mailing list, this issue is solved.  I had the following line in the global section of my smb.conf file:

valid users = %S 

That was left over from the original smb.conf file generated by Samba upon install.  I'm not using user shares, but I left it in case I might in the future.  Well, that was causing my issues with Win7.  As soon as I commented that out, Win7 was fine.  I have no clue why XP didn't mind it.

---

### Post by ShizzlePDX503 on 2010-06-10
I am glad that you were able to solve your issue and I wish I was more helpful but I am still pretty new to the Linux world and was trying to bounce ideas around.

---


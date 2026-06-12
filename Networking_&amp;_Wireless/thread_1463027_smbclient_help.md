---
title: "smbclient help"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by @mir on 2010-04-26
Hi,

i am trying to send message through terminal with smbclient, i have searched the net and found this command
```

smbclient -M <hostname>

```now i am confused on hostname, which i open the network folder i see to icons
1. is my laptop
2. Windows Network

when i enter Windows Network folder i see 2 more icons
1.MSHOME
2.WORKGROUP

and when i enter MSHOME folder i see one icon
1. MIRZA-SAAD

this is the computer which has xp in it i want to send message to it with smbclient

now how when i write this command i see this error

```

amir@amir-laptop:~$ smbclient -M //MSHOME/MIRZA-SAAD/
Connection to //MSHOME/MIRZA-SAAD/ failed. Error NT_STATUS_BAD_NETWORK_NAME

```now where am i making mistake i am stuck can come one help me

:(

---

### Post by bab1 on 2010-04-26
> **@mir said:**
> Hi,

i am trying to send message through terminal with smbclient, i have searched the net and found this command
```

smbclient -M <hostname>

```now i am confused on hostname...(

Actually the -M switch is for the netbios name.  It may or may not matter.  Use only the netbios name, not the //workgroup/netbios name.  From the man page:```
-M NetBIOS name
          This  options allows you to send messages, using the "WinPopup" pro-
          tocol, to another computer. Once a  connection  is  established  you
          then type your message, pressing ^D (control-D) to end.

          If  the receiving computer is running WinPopup the user will receive
          the message and probably a beep. If they are  not  running  WinPopup
          the message will be lost, and no error message will occur.

          The  message  is also automatically truncated if the message is over
          1600 bytes, as this is the limit of the protocol.

          One useful trick is to cat the message through smbclient. For  exam-
          ple:




          cat mymessage.txt | smbclient -M FRED

          will send the message in the file mymessage.txt to the machine FRED.

          You may also find the -U and -I options useful, as they allow you to
          control the FROM and TO parts of the message.

          See  the message command parameter in the smb.conf(5) for a descrip-
          tion of how to handle incoming WinPopup messages in Samba.
```

---

### Post by @mir on 2010-04-26
Thankx for ur reply 

but hostname is the computer name or what,

i xp when i check system properties and see the computer name it says "mirza-saad"

but it give me still error
```

amir@amir-laptop:/var/www$ smbclient -M mirza-saad
Connection to mirza-saad failed. Error NT_STATUS_BAD_NETWORK_NAME

```

tried this too
```

amir@amir-laptop:/var/www$ smbclient -M //mirza-saad
Connection to //mirza-saad failed. Error NT_STATUS_BAD_NETWORK_NAME
amir@amir-laptop:/var/www$ smbclient -M MIRZA-SAAD
Connection to MIRZA-SAAD failed. Error NT_STATUS_BAD_NETWORK_NAME
amir@amir-laptop:/var/www$ smbclient -M //MIRZA-SAAD
Connection to //MIRZA-SAAD failed. Error NT_STATUS_BAD_NETWORK_NAME

```

still no help, plz u give me a precise example which u have tried

---

### Post by bab1 on 2010-04-26
> **@mir said:**
> Thankx for ur reply 

but hostname is the computer name or what,


No they are not the same.  The term hostname is what Linux uses for naming and this is resolved by DNS.  The COMPUTER name is a NetBIOS name.  DNS servers can not resolve NetBIOS names.  That being said, both can be resolved if you have your network setup to resolve the names correctly.
> 

i xp when i check system properties and see the computer name it says "mirza-saad"

That is the NetBIOS (WINS) name.> 

but it give me still error
```

amir@amir-laptop:/var/www$ smbclient -M mirza-saad
Connection to mirza-saad failed. Error NT_STATUS_BAD_NETWORK_NAME

```

tried this too
```

amir@amir-laptop:/var/www$ smbclient -M //mirza-saad
Connection to //mirza-saad failed. Error NT_STATUS_BAD_NETWORK_NAME
amir@amir-laptop:/var/www$ smbclient -M MIRZA-SAAD
Connection to MIRZA-SAAD failed. Error NT_STATUS_BAD_NETWORK_NAME
amir@amir-laptop:/var/www$ smbclient -M //MIRZA-SAAD
Connection to //MIRZA-SAAD failed. Error NT_STATUS_BAD_NETWORK_NAME

```

still no help, plz u give me a precise example which u have tried

I'm not at a Linux host today so I have no opportunity to give you a positive answer.  But that is what experimenting is all about.  I can tell you that the command should be (with no \\) ```
smbclient -M mirza-saad
```
If you still have an error the problem is with your naming services and not the XP host or the smbclient.

---

### Post by @mir on 2010-04-26
Thankx for the reply

at this point i have a little understanding, but can u tell me how can u get the hostname of that computer which i want to send the message

is there any command which will list me the computer currently on the network with there hostname..

or is there any way to get the hostname.. 

thankx in advance

---

### Post by bab1 on 2010-04-26
> **@mir said:**
> Thankx for the reply

at this point i have a little understanding, but can u tell me how can u get the hostname of that computer which i want to send the message

is there any command which will list me the computer currently on the network with there hostname..

or is there any way to get the hostname.. 

thankx in advance

From the terminal you can use the command ```
smbstatus
```This will list all the hosts connected to shares that on the LAN that are up.


Here is what I get on my own personal lan:```
smbstatus

Samba version 3.0.28a
PID     Username      Group         Machine
-------------------------------------------------------------------
 4470   bruce         bruce         kona         (192.168.1.152)
 4466   bruce         bruce         malibu       (192.168.1.12)

Service      pid     machine       Connected at
-------------------------------------------------------
Backup       4466   malibu        Mon Apr 26 15:35:26 2010
Backup       4470   kona          Mon Apr 26 15:36:47 2010
IPC$         4464   malibu        Mon Apr 26 15:35:16 2010
IPC$         4463   malibu        Mon Apr 26 15:35:09 2010

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
4470         1000       DENY_NONE  0x100001    RDONLY     NONE             /smb/backup   .   Mon Apr 26 15:36:47 2010
```

Interestingly, I am not running a WINS server.  I rely on NetBIOS broadcasts for Vista and XP name resolution.  This means WinPopups don't work.  I can however connect to my DNS resolved Linux host.  See Below.

Trying to contact a Vista host```
smbclient -M kona
Connection to kona failed. Error NT_STATUS_BAD_NETWORK_NAME
``` 

Trying to contact a Linux host
```
smbclient -M malibu
message start: ERRSRV - ERRmsgoff (Not receiving messages.)
```

Some interesting thoughts.

[LIST]
[*]You must have a windows host for WinPopup to work
[*]You must run a WINS server ro resolve NetBIOS names for Windows hosts
[*]You must be connected to a share for you to send a message from the server (see smbstatus)
[/LIST]

EDIT:  I must correct myself.  You can recieve WinPopup on Samba clients.  See below.
> To handle incoming " WinPopup" messages on Linux, set the "message command" parameter in the smb.conf. 
    message command = csh -c 'xedit %s;rm %s' &
    
This will use the application "xedit" to display the message. The message is then removed.
%s : The filename containing the message.
%t : Message destination (computer or server to which it was sent.)
%f : Message sender.
Default smb.conf config file is no message command.
Notes:

Using mail to relay the incoming message. Linux smb.conf: 
    message command = /bin/mail -s 'message from %f on %m' root < %s; rm %s

[SIZE="1"]From: [_http://www.yolinux.com/TUTORIALS/LinuxTutorialMicrosoftWindowsNetworkIntegration.html_]("http://www.yolinux.com/TUTORIALS/LinuxTutorialMicrosoftWindowsNetworkIntegration.html")[/SIZE]
    

---

### Post by @mir on 2010-04-27
Thankx a lot buddy

i will work in it little more, and see what happens

one more question it there is a ubuntu pc on the network we can send message by

"write" command,

is there any command to see list of linux machine on the network

i found this command
```

**write <username> **
for example
**write george** (where george is a valid user in the system or the network)
press **enter**
type in the **message** and press **enter**
press **ctrl-C** to end the message

```

but to user this command i have to see the list of other linux machines on the network

can u help me here too

---

### Post by bab1 on 2010-04-27
> **@mir said:**
> Thankx a lot buddy

i will work in it little more, and see what happens

one more question it there is a ubuntu pc on the network we can send message by

"write" command,

is there any command to see list of linux machine on the network

i found this command
```

**write <username> **
for example
**write george** (where george is a valid user in the system or the network)
press **enter**
type in the **message** and press **enter**
press **ctrl-C** to end the message

```

but to user this command i have to see the list of other linux machines on the network

can u help me here too

Not that I know of.

---


---
title: "mount.cifs ntlmv2  INVALID_PARAMETER?"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by briwood on 2009-08-04
man 8 mount.cifs says sec=ntlmv2 is a valid option. Can anyone tell me why I'm seeing this:

```
joeuser@joeuser-vmware02:~$ sudo /sbin/mount.smbfs //campus.example.com/cois test-o --verbose -o credentials=/home/joeuser/joeuser.txt,sec=ntlmv2

parsing options: credentials=/home/joeuser/joeuser.txt,sec=ntlmv2

 

mount.cifs kernel mount options unc=//campus.example.com\cois,ip=000.000.000.000,user=joeuser,pass=xxx,ver=1,credentials=/home/joeuser/joeuser.txt,sec=ntlmv2

mount error 22 = Invalid argument

Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```
 
/var/log/messages:

```
Aug  4 10:28:42 joeuser-vmware02 kernel: [85825.287792] Status code returned 0xc000000d NT_STATUS_INVALID_PARAMETER
```

If I remove ',sec=ntlmv2' from the mount command, I get "logon failure" because ntlmv2 is required.  I have  

 ```
client ntlmv2 auth = yes
```

in smb.conf and leaving it off the command line, but I still get a logon failure.

What really puzzels me is that I can connect with smbclient using the same credentials:

```
joeuser@joeuser-vmware02:~$ smbclient //campus.example.com/cois  -A ~/joeuser.txt
Domain=[CAMPUS] OS=[Windows Server (R) 2008 Standard 6002 Service Pack 2] Server=[Windows Server (R) 2008 Standard 6.0]
smb: \>
```


I'm on 8.04 LTS server: 
kernel: 2.6.24-24-server
smbstatus: Samba version 3.0.28a

Thanks for any help.

---

### Post by briwood on 2009-08-05
I'm thinking that I am lacking some package for ntlmv2 and ntlmv2i.  if I use sec=ntlm I don't get the invalid parameter.

---

### Post by briwood on 2009-08-06
The problem was that I was specifying a DFS mount where I didn't have windows permissions.   This was resulting in "mount error 22 = Invalid argument" which I was interpreting as "CIFS is missing a library or something and can't use ntlmv2."

Here are the mapped drives on my windows box.  I was trying to get to O:\


    ```
H:\>net use
    New connections will be remembered.


    Status       Local     Remote                    Network

    -------------------------------------------------------------------------------
                 G:        \\campus.example.com\jkl\COIS
                                                    Microsoft Windows Network
                 H:        \\campus.example.com\Home\joeuser
                                                    Microsoft Windows Network
    Disconnected I:        \\000.000.000.000\c$       Microsoft Windows Network
    Disconnected J:        \\secure\inetpub$         Microsoft Windows Network
                 O:        \\campus.example.com\cois
                                                    Microsoft Windows Network
    OK           T:        \\devwww.example.com\c$
                                                    Microsoft Windows Network
    The command completed successfully.

```

It occured to me just now to try to mount a different target, T:\ (above)

    ```
joeuser@joeuser-vmware02:~$ sudo mount -t cifs //foo.bar.example.com/c$ test-o -ouser=CAMPUS/joeuser,sec=ntlmv2
    Password:
    joeuser@joeuser-vmware02:~$

```

***I did not get the "invalid parameter" error when using sec=ntlmv2!  And it worked!***
```

    joeuser@joeuser-vmware02:~$ ll test-o/
    total 786873
    drwxrwxrwx 1 root  root          0 2009-01-28 04:20 ./
    drwxr-xr-x 9 joeuser joeuser      4096 2009-08-05 15:51 ../
    -rwxrwSrwx 1 root  root          0 2005-11-02 17:36 AUTOEXEC.BAT*
    -r-xr-Sr-x 1 root  root        208 2007-12-07 08:08 boot.ini*
    drwxrwxrwx 1 root  root          0 2009-01-28 04:25 Config.Msi/
    -rwxrwSrwx 1 root  root          0 2005-11-02 17:36 CONFIG.SYS*
    drwxrwxrwx 1 root  root          0 2009-05-26 12:47 Documents and Settings/
```


Here's how to find out the correct way to map to the O: drive:

Windows Explorer: right-click O:\ and choose Properties > DFS.  Determine the active path. For me it was "foo.bar.example.com/COIS"

Now browse to that path in Explorer.  Right click on a sub dir that you are pretty sure that you have access to: Properties > DFS. Copy the path appearing in the text box at the top of this tab.

Paste the path into your terminal and convert "\" to "/" to create your mount command:

```
joeuser@joeuser-vmware02:~$sudo mount -t cifs //foo.bar.example.com/COIS/FTP/COIS/backup test3 -ouser=CAMPUS/joeuser,sec=ntlmv2
joeuser@joeuser-vmware02:~$ cd test3
joeuser@joeuser-vmware02:~/test3$ mkdir somehost
joeuser@joeuser-vmware02:~/test3$ ll
total 4
drwxrwxrwx  1 root  root     0 2009-08-06 10:34 ./
drwxr-xr-x 12 joeuser joeuser 4096 2009-08-06 10:32 ../
drwxr-xr-x  2 root  root     0 2009-08-06 10:34 somehost/
```

Enjoy.

---

### Post by briwood on 2009-08-06
Not sure how to edit the title so it reads "[SOLVED]" when you are looking at the forum listing....

---

### Post by Iowan on 2009-08-07
You can change post titles, or include a "solved" tag, but only moderators (or so I've read) can change thread title. [http://ubuntuforums.org/showthread.php?t=1044714]("http://ubuntuforums.org/showthread.php?t=1044714")

---


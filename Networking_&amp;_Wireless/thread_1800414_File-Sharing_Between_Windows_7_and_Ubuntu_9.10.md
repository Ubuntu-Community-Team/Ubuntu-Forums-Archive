---
title: "File-Sharing Between Windows 7 and Ubuntu 9.10"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Jesdisciple on 2011-07-08
I'm trying to upgrade to Ubuntu 11.04 via Unetbootin, but for some reason I can never download an uncorrupted ISO.  I have Windows 7 on a separate computer (It's for work, I promise! :p) so I decided to try downloading on that and it worked.  But my only available USB drive isn't large enough for the transfer, so I'm trying to set up file-sharing which, from the coverage I've seen in forums and articles, shouldn't be very difficult.  But I don't even have the two seeing each other.

So if I could have help setting it up on the Ubuntu end that would be great.  If someone can help with Windows that would be nice too, but I have no problems with going to a Windows forum for that.  (I'm just using 7's inbuilt support for sharing, as that seems like standard practice and I couldn't find a Samba client for recent Windows versions.)

In network:/// I find an inode called "Windows Network" which leads to smb:///.  This further contains an inode named "WORKGROUP," but trying to open it renders a message that "Unable to mount location - Failed to retrieve share list from server."  Windows just doesn't list any neighbors.  Help!
```
$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.69    JESDISCIPLE-LAP [WORKGROUP] [Unix] [Samba 3.4.0]
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by pastalavista on 2011-07-09
Open Synaptic Package Manager, search for 'samba', and make sure you have all the necessary components installed, especially 'winbind'

---

### Post by Jesdisciple on 2011-07-09
I got seven packages returned as results for that search, including those you listed.  For completeness, I got them via the terminal so I can paste them.  Interestingly, smbclient and libwbclient0 were not common to the two searches, so I listed both here.```
$ aptitude search '~i' | grep -i samba
i   libpam-smbpass                  - pluggable authentication module for Samba 
i   libwbclient0                    - Samba winbind client library              
i   python-smbc                     - Python bindings for Samba clients (libsmbc
i   samba                           - SMB/CIFS file, print, and login server for
i   samba-common                    - common files used by both the Samba server
i   samba-common-bin                - common files used by both the Samba server     
i   smbclient                       - command-line SMB/CIFS clients for Unix 
i A winbind                         - Samba nameservice integration server   
```

---

### Post by Jesdisciple on 2011-07-12
I found my larger USB drive, so I don't need Samba yet.  I might try again after updating Ubuntu.  The larger issue continues [here]("http://ubuntuforums.org/showthread.php?t=1802748").

---


---
title: "cannot share folders between two ubuntu machines"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by scmcgraw on 2011-12-08
Hi Folks,
I am having trouble sharing folders between two ubuntu machines using Samba. It used to work and now doesn't. The major change i made was I stopped using ICS and I'm now connected to a fixed line for broadband instead of a dongle.

I have two machines running 10:10 one of which has an external drive connected to it so i can watch movies on the other machine through the TV. the one with the external drive is call mainpc and the one connected to the tv is called minidesktop. I did a findsmb and just to note it was very slow to find the shares. not sure if this is an indication of something?

scott@ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.2.3     MAINPC        +[    WORKGROUP     ]
192.168.2.4     SCOTT-MINIDESKT [    WORKGROUP     ]
scott@ubuntu:~$ 

Next i ran the smbtree and i am seeing connection issues: this was also slow to pull data.

scott@ubuntu:~$ smbtree
Enter scott's password: 
WORKGROUP
    \\SCOTT-MINIDESKT        scott-minidesktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to SCOTT-MINIDESKT<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\MAINPC                 mainpc server (Samba, Ubuntu)
cli_start_connection: failed to connect to MAINPC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
scott@ubuntu:~$ 


any help in getting my sharing working would be much appreciated.

cheers scott

---


---
title: "FTP Server in Ubuntu (vsftpd) help"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-02-24
[http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

I followed the directions there but it doesn't work, I cannot even FTP localhost on here, let alone from the internet!

---

### Post by cybergalvez on 2009-02-25
> **RealG187 said:**
> [http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

I followed the directions there but it doesn't work, I cannot even FTP localhost on here, let alone from the internet!

ssh is easier to set up and will do sftp

---

### Post by RealG187 on 2009-02-25
> mpg@MIKED6:~$ ftp localhost
Connected to localhost.
500 OOPS: vsftpd: both local and anonymous access disabled!
ftp> 

I got something, maybe I can't FTP from localhost (dunno why, that's the best way to test it)

---

### Post by superprash2003 on 2009-02-25
its to do with your vsftpd settings.. you could try gproftpd, easy to setup.. its an ftp server.. it has a GUI

---

### Post by RealG187 on 2009-02-25
How can I change the folder that is the root for the FTP server I do not want "/" as the FTP folder, I want "/home/mpg/Desktop/Incoming/FTP"

EDIT: WTF if I ftp "localhost" or "Miked6" from my machine (mike6 is my hostname) I get the root folder (/), but if I ftp miked6 from another machine on my network I get my home folder.

---

### Post by RealG187 on 2009-02-26
> C:\Users\Mike>ping [color=red]My Home IP[/color]

Pinging [color=red]My Home IP[/color] with 32 bytes of data:
Reply from [color=red]My Home IP[/color]: bytes=32 time=76ms TTL=252
Reply from [color=red]My Home IP[/color]: bytes=32 time=206ms TTL=252
Reply from [color=red]My Home IP[/color]: bytes=32 time=372ms TTL=252
Reply from [color=red]My Home IP[/color]: bytes=32 time=166ms TTL=252

Ping statistics for [color=red]My Home IP[/color]:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 76ms, Maximum = 372ms, Average = 205ms

I cannot FTP into my Machine from the internet, I have ports 20 and 21 forwarded on my router, this is what I get when I ping my home IP from outside my network.

---

### Post by MR_MUSHROOM on 2009-02-28
ok this is my first reply on this place :)

i am sitting down with vsftpd myself and what i found out is this tutorial

[http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/](http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/)

i am not 100% SURE about the configuration file /etc/vsftpd/vsftpd-virtual.conf.

there is allot of different configs on this one on the net :) fun right.

This is a new started wiki
[http://viki.brainsware.org/?en/Virtual_Hosts_Users](http://viki.brainsware.org/?en/Virtual_Hosts_Users)

in this part of the vsftpd-virtual.conf file you can redirect were ever
you want in your computer (important this is my understanding i might be wrong.)
________________________________________________________
# in conjunction with 'local_root',
# specifies a home directory for each virtual user
user_sub_token=$USER
local_root=/var/www/virtual/$USER
===================================
change the above line to local_root=/home/user/Desktop/where/u/want/
===================================
_________________________________________________________

my problem were to create the db-file (DataBase-file) with he line

# sudo db_load -T -t hash -f virtual-users.txt /etc/vsftpd/virtual-users.db

i found the problem to hardy simular to most distro i think :)
solution:
sudo apt-get install db4.6-util
sudo db4.6_load -T -t hash -f logins.txt /etc/vsftpd_login.db

The db_load should be db4.6_load (the db_load version).

but am not don with my problems i cant change owner to ftp:ftp by command sudo chown ftp:ftp /My/FTP/FOLDER/.

best of luck.

---

### Post by MR_MUSHROOM on 2009-02-28
This should work. Is did fore me. i am up and running the server with 3 virtual users and more are coming :)

==========================================================================

 Setup of VSFTPD virtual users

If you are hosting several web sites, for security reason, you may want the webmasters to access their own files only. One of the good way is to give them FTP access by setup of VSFTPD virtual users and directories. This article describes how you can do that easily.
(See also: Setup of VSFTPD virtual users - another approach)

1. Installation of VSFTPD

    # sudo apt-get install vsftpd

2. Virtual users and authentication

We are going to use pam_userdb to authenticate the virtual users. This needs a username / password file in `db&#8217; format - a common database format. We need `db_load&#8217; program.

    # sudo apt-get install db4.6-util    | vid skrivande stund.


To create a `db&#8217; format file, first create a plain text file `virtual-users.txt&#8217; with the usernames and passwords on alternating lines:

    mary
    123456
    jack
    654321

Then execute the following command to create the actual database:

    # sudo db4.6_load -T -t hash -f virtual-users.txt /etc/vsftpd/virtual-users.db

Now, create a PAM file /etc/pam.d/vsftpd-virtual which uses your database:

    auth required pam_userdb.so db=/etc/vsftpd/virtual-users
    account required pam_userdb.so db=/etc/vsftpd/virtual-users

3. Configuration of VSFTPD

Create a configuration file /etc/vsftpd/vsftpd-virtual.conf,

    # disables anonymous FTP
    anonymous_enable=NO
    # enables non-anonymous FTP
    local_enable=YES
    # activates virtual users
    guest_enable=YES
    # virtual users to use local privs, not anon privs
    virtual_use_local_privs=YES
    # enables uploads and new directories
    write_enable=YES
    # the PAM file used by authentication of virtual uses
    pam_service_name=vsftpd-virtual
    # in conjunction with 'local_root',
    # specifies a home directory for each virtual user
    user_sub_token=$USER
    local_root=/home/ftp/$USER
    # the virtual user is restricted to the virtual FTP area
    chroot_local_user=YES
    # hides the FTP server user IDs and just display "ftp" in directory listings
    hide_ids=YES
    # runs vsftpd in standalone mode
    listen=YES
    # listens on this port for incoming FTP connections
    listen_port=60021
    # the minimum port to allocate for PASV style data connections
    pasv_min_port=62222
    # the maximum port to allocate for PASV style data connections
    pasv_max_port=63333
    # controls whether PORT style data connections use port 20 (ftp-data)
    connect_from_port_20=YES
    # the umask for file creation
    local_umask=022

4. Make userfolder red/write/delite able.

    # cd /home/ftp
    # sudo mkdir mary
    # sudo chmod 777 mary/

5. Restart the FTP by command.

    # sudo /etc/init.d/vsftpd restart

6. login localy to your FTP server by:

    # ftp localhost
           or
    # ftp 192.168.1.100 (your ip on the network)
==========================================================================

Best of luck.

EDIT:

add some personal touch to login :) OPTIONAL

in /etc/vsftpd/vsftpd-virtual.conf

im using kde (kubuntu) an add a new line to:

    # kdesudo kate /etc/vsftpd/vsftpd-virtual.conf

ftpd_banner=WELCOME TO ---===_MUSHROOM&#346;_===--- FTP.

The welcome text will show on login :)

---

### Post by RealG187 on 2009-03-02
I am using gproftpd but I can't find the GUI.

I can connect from localhost or XP, I tried connecting from my Windows Mobile PDA phone (from withing my network using Wifi, and outside over 3G internet) without sucess :(

---

### Post by MR_MUSHROOM on 2009-03-03
Take a look on this page.

[http://www.howtoforge.com/proftpd_web_interface_gui_tools](http://www.howtoforge.com/proftpd_web_interface_gui_tools)

* Administrator
* Management

that i think will fit your diskription.

---

### Post by RealG187 on 2009-03-03
> **MR_MUSHROOM said:**
> Take a look on this page.

[http://www.howtoforge.com/proftpd_web_interface_gui_tools](http://www.howtoforge.com/proftpd_web_interface_gui_tools)

* Administrator
* Management

that i think will fit your diskription.
Do I have to install another package to get a GUI?

---

### Post by RealG187 on 2009-03-16
I can connect from inside my LAN but not from the internet even though I have ports 20 and 21 forwarded.

---

### Post by RealG187 on 2009-04-29
I setup DMZ on the computer and I think it works, but I dont wanna have to have this computer in DMZ mode, I would just wanna forward the ports, but forwarding ports 20 and 21 don't work...

---

### Post by dmizer on 2009-05-02
You will need more than port 20 and 21 forwarded. See the 3rd link in my signature for more information.

---

### Post by RealG187 on 2009-05-02
> **dmizer said:**
> You will need more than port 20 and 21 forwarded. See the 3rd link in my signature for more information.

I have DMZ on (isn't that all ports forwarded) and it still doesn't work :(

---

### Post by dmizer on 2009-05-02
When you test, are you actualy outside of your lan, or are you just trying to use your external IP from inside your lan?

If you havn't tested from outside your lan, try it. You may already be working.

If not, you should still look at the FTP howto in my sig.

---

### Post by RealG187 on 2009-05-04
I was testing from outside my LAN.

It actually works inside my lan (by using my external/DMZ IP) but not from outside.

---

### Post by t4thfavor on 2009-07-16
I used proftpd, and I will post my config file, note I had to remove my IP, and that I also had to forward the pasive port range on my router.

Works from inside, and outside using my public hostname.

---

### Post by RealG187 on 2009-07-16
Is there one with a GUI? I tried a few and I never got them working, well I did but I think I had two at the same time running so I would get different folders.

It worked inside but not outside, I even tried setting DMZ on my computer...

---


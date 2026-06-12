---
title: "HowTo: Using Conky on any ubuntu box to view recording info on backend."
date: 2008-09-30
forum: Mythbuntu
---

### Post by DemonBob on 2008-09-30
This is a How-To on using conky on any ubuntu box to view recording info on your backend. This is accomplised by install mythtv-status on the ubuntu box that uses conky. I've modified mythtv-status a little bit.

For none, ubuntu distrobutions, you can find mythtv-status here. [http://www.etc.gen.nz/projects/mythtv/mythtv-status.html](http://www.etc.gen.nz/projects/mythtv/mythtv-status.html)


1. Copy your /home/username/.mythtv/config.xml from your mythbuntu box to your local ubuntu desktop /home/username/.mythtv/config.xml

2. Edit the config.xml file to reflect the ip address of your backend 
```
gedit ~/.mythtv/config.xml
```

Edit this line. Change localhost to the ip address of your backend. In my case
```
<DBHostName>localhost</DBHostName>
```

Changed to: 

```
<DBHostName>192.168.15.3</DBHostName>
```

3. Link config.xml to /root/.mythtv/config.xml

```
sudo mkdir /root/.mythtv
sudo ln -s ~/.mythtv/config.xml /root/.mythtv/config.xml
``` 

This is to fix the perl api warning in mythtv status. 

4. Install mythtv-status
```
sudo apt-get update
sudo apt-get install mythtv-status
```

5. Edit mythtv-status to reflect my changes. 

```
sudo gedit /usr/bin/mythtv-status
```

Around line 21. Change localhost to ip address of backend

```
my $host = "localhost";
```

In my instance it changes to. 

```
my $host = "192.168.15.3";
```

6. Edit .conkyrc file to add output. 

```
gedit ~.conkyrc
```

Near the top, add

```
text_buffer_size 1024
```


At the bottom add

```
${color #0077ff} ${execi 300 perl /usr/bin/mythtv-status KISP}
```

Change the colors to correspond to your current .conkyrc config. 


Run conky to test.

---

### Post by DemonBob on 2008-09-30
Screenshot of the output.

---

### Post by lime4x4 on 2008-10-19
followed your how to and i'm still getting that api error any ideas?
I'm running intrepid on the conky box

---

### Post by lime4x4 on 2008-10-19
followed your how to and i'm still getting that api error any ideas?
I'm running intrepid on the conky box

---

### Post by DemonBob on 2008-10-19
> **lime4x4 said:**
> followed your how to and i'm still getting that api error any ideas?
I'm running intrepid on the conky box

Hmm, i'm using Intrpeid also, and it's working fineu since alpha 6

Could you compare the output of /root/.mythtv/config.xml, and /home/your_username/.mythtv/config.xml

---

### Post by lime4x4 on 2008-10-20
there the same

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>f424a9a0-329f-4106-baa8-196d72b816b3</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.1.100</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>Hf5Vs6a5</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

---

### Post by DemonBob on 2008-10-21
Try running conky from the command line to see what errors it produces, aftwards run /usr/bin/mythtv-status from the command line, post the output of both.

---

### Post by lime4x4 on 2008-10-21
john@john-desktop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (1a00157) is subwindow of root window (117)
Conky: window type - override
Conky: drawing to created window (0x5000004)
Conky: drawing to double buffer


john@john-desktop:~$ /usr/bin/mythtv-status

MythTV status for 192.168.1.100
===============================
Status...........: Tue Oct 21 2008, 8:00 PM
Total Disk Space.: Total space is 110,503 MB, with 88,246 MB used (79.9%)
Next Recording In: 47 Hours, 59 Minutes

Encoders:
john-mythtv (1) - Idle

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why.

---

### Post by lime4x4 on 2008-10-22
john@john-desktop:~$ /usr/bin/mythtv-status --verbose
DBI connect('database=mythconverg:host=192.168.1.100;port=3306','mythtv',...) failed: Can't connect to MySQL server on '192.168.1.100' (111) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database: 

We have the correct protocol version for Total Disk Space
We have the correct xml version for Total Disk Space
We have the correct protocol version for Total Disk Space
We have the correct protocol version for Disk Space

MythTV status for 192.168.1.100
===============================
Status...........: Wed Oct 22 2008, 5:17 PM
Total Disk Space.: Total space is 110,503 MB, with 88,246 MB used (79.9%)
Next Recording In: 26 Hours, 42 Minutes

Encoders:
john-mythtv (1) - Idle

Scheduled Recordings:
2008-10-23 20:00:00 - Survivor: Gabon (KYW)

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why.

john@john-desktop:~$

---

### Post by tom.weingarten on 2008-10-23
I fixed this problem by running "ssh hostname mythtv-status". In other words I'm running mythtv-status on the mythtv backend. This only works if you have ssh keys set up, but that's easy enough.

---

### Post by lime4x4 on 2008-10-23
what changes do i have to make to use the ssh method

---

### Post by lime4x4 on 2008-10-26
i can ssh into my myth box but when i run the command it asks for a password
which i have to type in. Any way around this?

---

### Post by lime4x4 on 2008-10-26
i got it to use the ssh keys but it's still giving me an error yet

john@john-desktop:~$ /usr/bin/mythtv-status --verbose
DBI connect('database=mythconverg:host=ssh 192.168.1.100 mythtv-status;port=3306','mythtv',...) failed: Unknown MySQL server host 'ssh 192.168.1.100 mythtv-status' (1) at /usr/share/perl5/MythTV.pm line 337
Cannot connect to database:

---

### Post by lime4x4 on 2008-10-27
but i can run the following command and it works

john@john-desktop:~$ ssh 192.168.1.100 mythtv-status

MythTV status for localhost
===========================
Status...........: Sun Oct 26 2008, 11:59 PM
Total Disk Space.: Total space is 110,503 MB, with 91,476 MB used (82.8%)
Next Recording In: 44 Hours,

Encoders:
john-mythtv (1) - Idle

---

### Post by DemonBob on 2008-10-27
You know, now thinking about it my mythbackend might be configured a bit differently then everyone elses.

---

### Post by dakota34 on 2009-09-13
thanks so much! worked perfectly. This is awesome.:D

---

### Post by DemonBob on 2010-08-29
I am updating this how-to soon. I'm doing work on customising the mythtv-status perl script so it will be easier to change colors by modifying a couple of variable's at the top of it. I hope on posting the file in a day or two. All you will have to do is download mythtv-status-conky and place it beside mythtv-status. Then change a few options in the file as far as color and such. Should make everything flow better, and allow better color matching to your current conky config. 

Screenshot below.

---


---
title: "ALSA not working"
date: 2011-05-09
forum: Multimedia Software
---

### Post by stephenstop on 2011-05-09
I have ubuntu 10.04,alsa stopped working as did pulse audio,i am new to this and super confused.

---

### Post by handy on 2011-05-10
Have you run alsamixer in the Terminal to see what it is set at?

---

### Post by stephenstop on 2011-05-13
yea but i dont understand what u mean by "set at",im trying to use jack audio too,but no one seems to know ,could you help me
stephen

---

### Post by lidex on 2011-05-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by stephenstop on 2011-06-03
```


owner@owner-laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2011-06-03 06:35:54--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8008 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-fYnXOR/Packages'

100%[======================================>] 8,008       --.-K/s   in 0.1s    

2011-06-03 06:35:54 (79.6 KB/s) - `/tmp/dvdcss-fYnXOR/Packages' saved [8008/8008]

--2011-06-03 06:35:54--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-fYnXOR/libdvdcss.deb'

100%[======================================>] 38,036       103K/s   in 0.4s    

2011-06-03 06:35:55 (103 KB/s) - `/tmp/dvdcss-fYnXOR/libdvdcss.deb' saved [38036/38036]

(Reading database ... 231443 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-fYnXOR/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
owner@owner-laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-06-03 06:44:35--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-06-03 06:44:37--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      71.7K/s   in 0.4s    

2011-06-03 06:44:38 (71.7 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.




```

---

### Post by lidex on 2011-06-03
The terminal output should supply you with an actual url for alsa-info. Post that please.

---

### Post by stephenstop on 2011-06-14
```

 http://www.alsa-project.org/alsa-info.sh



```

---

### Post by stephenstop on 2011-06-14
```

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.




```


it said this at the end,please help me

---

### Post by lidex on 2011-06-15
OK then, don't upload - select n - and post the contents of the resulting textfile in your /tmp directory into your next post. Make sure to enclose the text in code tags.

---

### Post by stephenstop on 2011-06-17
```
See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : n


Your ALSA information is in /tmp/alsa-info.txt.bX0h6gdlo8





```

---

### Post by lidex on 2011-06-18
> **stephenstop said:**
> ```
See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : n


Your ALSA information is in /tmp/alsa-info.txt.bX0h6gdlo8





```

Sorry, I can't read your hard drive. You'll need to physically open that file then copy and paste contents into your post or upload the file as an attachment.

---

### Post by stephenstop on 2011-06-19
so nowwhat???/?????

---

### Post by Yellow Pasque on 2011-06-19
Run the script again. Upload the info this time and post the link (or post the contents of the tmp file)
```
gedit /tmp/alsa-info.txt.*
```

---


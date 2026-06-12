---
title: "webcam (program) and  motion problems"
date: 2012-01-20
forum: Multimedia Software
---

### Post by SoFl W on 2012-01-20
I decided to concentrate on one problem at a time so I am re-writing this question.  I am having problems with the webcam program.

this is my .webcamrc file
```

[grab]
device = /dev/video0
text = "Front camera %b-%d-%y %I:%M:%S%P"
#infofile = front.jpg
fg_red = 255
fg_green = 255
fg_blue = 255
# With the new pcw-driver (see on top of this page) even 640x480 is possible!
width = 640
height = 480
delay = 900
wait = 1
#input = composite1
#norm = ntsc
rotate = 0
top = 0
left = 0
bottom = -1
right = -1
quality = 75
trigger = 180
once = 1
#archive front%b-%d-%y_%I:%M:%S%P

[ftp]
host = www.mysitename.com
user = username
password = xxxxx
dir  = /webcam
file = front.jpg
tmp  = uploading.jpeg
passive = 1
debug = 1
auto = 1
local = 0
ssh = 0

```This is the output I get:
```
soflw@soflw-desktop:~$ webcam
reading config file: /home/soflw/.webcamrc
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
[ftp]<< ftp> 
[ftp]>> pass
[ftp]<< pass
[ftp]<< Passive mode on.
[ftp]<< ftp> 
[ftp]>> close
[ftp]<< close
[ftp]<< Not connected.
ftp: lost connection
[ftp]<< ftp> 
[ftp]>> open www.mysitename.com
[ftp]<< open www.mysitename.com
[ftp]<< Connected to mysitename.com.
[ftp]<< 220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
[ftp]<< 220-You are user number 3 of 75 allowed.
[ftp]<< 220-Local time is now 18:35. Server port: 21.
[ftp]<< 220-This is a private system - No anonymous login
[ftp]<< 220 You will be disconnected after 3 minutes of inactivity.
[ftp]<< Name (www.mysitename.com:soflw): 
^C

```(It just sits there until I ctrl-c out)

I would prefer to use ssh but that keeps asking my to manually enter my password, when I do it says it is wrong.  (I triple checked)

It does not transfer any files and I don't know where it would store the temporary file locally. I don't understand is why it adds the ":soflw" at the end of the last line.  It seems to pass my ubuntu username.

I could write my own script and use scp to transfer an image if I had a program to capture an image every xx minutes and write it to somewhere on the drive.

So does anybody have "webcam" (the program) working? preferably in ssh mode.  Or does anybody have another suggestion for a way to get one picture and transfer it to a remote server?

Edit:  In the webcamrc file, it still tries passive mode if I have passive set to 1 or 0.

(My other question was with "motion" but that doesn't seem to play nicely with my current desktop and 10.4.  I was able to get motion version 3.2.12 to work with 11.4 on my laptop, but I have not written a script to transfer a single image yet. I have had other problems with motion that I would like to ask about once I get this problem solved)

---

### Post by SoFl W on 2012-01-21
I think I solved my problem.  My hosting company allows you to create FTP users and allow them access to certain directories.  I didn't know how the FTP logged in, but the hosting company considers whatever directory the FTP user has access to the "/" directory.  I was using the absolute (full) path in the configuration.  This is why it wouldn't allow me to log in, I was trying to switch to a directory the FTP automated script didn't have access to.

I ended up switching to a capture program called [fswebcam]("http://www.r3uk.com/index.php/home/38-software/100-webcam-capture-using-fswebcam") and using [ncftpput]("http://www.ncftp.com/") to upload my image to the server. Two programs in one script, but this seems to work best for me at this time.

Now I just have to write the script to run fswebcam followed by ncftpput and have cron run that scipt every half hour.

Thank you to anyone that bothered to look at my question.

---


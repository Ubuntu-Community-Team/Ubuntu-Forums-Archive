---
title: "SHOUTcast  streaming"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by le1 on 2008-03-23
Here is how to setup SHOUTcast sever & stream your music.

I'm going to do most of it in terminal.

first go to:
[http://www.shoutcast.com/download/files.phtml](http://www.shoutcast.com/download/files.phtml)

download:
sc_serv_1.9.8_Linux.tar.gz (SHOUTcast Linux server (glibc) v...)
(i assume you'll have it on your desktop)

in terminal:
sudo (type password)
next:
cd /
next:
cd home/your-user-name (i.e. y-u-n)
next:
mkdir shoutcast
next:
cd shoutcast
next:
cp home/y-u-n/Desktop/sc_serv_1.9.8_Linux.tar.gz home/y-u-n/shoutcast
next:
tar -zxvf sc_serv_1.9.8_Linux.tar.gz
next:
you shoud have 3 files: README.TXT, sc_serv, sc_serv.conf
next:
gedit sc_serv.conf
next:
set few things:
MaxUser=32 (how many ppl can connect)
Password=changeme (set your pass)
rest you can leave as it is, save file, exit.
next:
download another file:
go to: [http://www.shoutcast.com/download/broadcast.phtml#posixdownload](http://www.shoutcast.com/download/broadcast.phtml#posixdownload)
grab: sc_trans_posix_040.tgz
next:
cp home/y-u-n/Desktop/sc_trans_posix_040.tgz home/y-u-n/shoutcast
next:
tar -zvxf sc_trans_posix_040.tgz
next:
cd sc_trans_040  
next:
gedit sc_trans.conf
next:
adjust few things: 
PlaylistFile=example.lst 
create playlist of your favs mp3s with e.g. vlc, name it myfavs.lst
in place of "example.lst" put your playlist file name i.e. myfavs.lst
(if you have it on your Desktop, it should go like this: home/y-u-n/Desktop/myfavs.lst)
next:
go to: [http://checkip.dyndns.org/](http://checkip.dyndns.org/) to check your IP
next:
ServerIP=myserver.com 
replace myserver.com with your IP
next:
Password=yourpassword (put the same pass you used few minutes ago)
next:
Bitrate=80000 ---> Bitrate=96000
Channels=1 ---> Channels=2
next:
save file, exit
next:
cd ..
./sc_serv
next:
open another terminal:
sudo, type pass
cd /
cd home/y-u-n/shoutcast/sc_trans_040
./sc_trans_linux
next:
CTRL+L in Audacious type [http://yourIP:8000](http://yourIP:8000), open
should work, all done.

I hope this was helpful.
Have a great day!

---

### Post by nutz on 2008-03-23
Might be a good idea to make mention of the legal requirements surrounding this. Streaming your Music over the internet without the proper license is treated the same as sharing it out on a P2P network.

---


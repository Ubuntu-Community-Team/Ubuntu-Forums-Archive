---
title: "url radios - plugins..."
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by spamalot on 2008-02-26
Hi all,

Most (not all) online radios I try to listen to give an error such as

12:42:04 PM: xine: couldn't find demux for >http://click.real.com/?pageid=radio.blues-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F7003528<
12:42:04 PM: input_http: 3xx redirection: >302 Moved Temporarily<
12:42:03 PM: xine: found input plugin : http input plugin

it doesn't matter if i use Kaffeine or MPlayer etc.

Pls help.

---

### Post by xc3RnbFO8P on 2008-02-26
Try this:

> [http://ubuntuforums.org/showthread.php?t=616353](http://ubuntuforums.org/showthread.php?t=616353)

---

### Post by spamalot on 2008-02-26
Thanks.

I followed the steps in Medibuntu (see below). Then the updates available flag showed up on the top right corner of the screen. I went ahead with the updates, Still no luck:

02:12:13 PM: xine: couldn't find demux for >http://click.real.com/?pageid=radio.blues-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F6964163<
02:12:13 PM: input_http: 3xx redirection: >302 Moved Temporarily<
02:12:13 PM: xine: found input plugin : http input plugin

Steps I have followed:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for er:
Sorry, try again.
[sudo] password for er:
--14:02:33--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

14:02:33 (21.43 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

er@ubuntu:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58.5kB]                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]              
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [71.1kB]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [241kB]        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages [4031B]     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages [241kB]           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]      
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [12.8kB]         
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [5915B]      
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [43.5kB]    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2901B]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4031B]  
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [9977B]     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [67.8kB]        
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [67.9kB]      
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources [937B]       
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources [67.8kB]           
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources [1883B]      
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources [10.6kB]       
Get:29 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Get:30 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2718B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Get:31 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages [5880B]
Get:32 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages [2559B]
Fetched 1034kB in 5s (173kB/s)  
Reading package lists... Done
er@ubuntu:~$ sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list
er@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  regionset
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 36.9kB of archives.
After unpacking 111kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free libdvdcss2 1.2.9-2medibuntu4 [36.9kB]
Fetched 36.9kB in 0s (56.8kB/s)
Selecting previously deselected package libdvdcss2.
(Reading database ... 173651 files and directories currently installed.)
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.9-2medibuntu4_amd64.deb) ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
er@ubuntu:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package w64codecs
er@ubuntu:~$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
--14:08:32--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

14:08:32 (21.66 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

er@ubuntu:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 194B in 0s (229B/s)
Reading package lists... Done
er@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
er@ubuntu:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  w64codecs
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 226kB of archives.
After unpacking 655kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free w64codecs 20061203-0medibuntu2 [226kB]
Fetched 226kB in 0s (239kB/s)     
Selecting previously deselected package w64codecs.
(Reading database ... 173660 files and directories currently installed.)
Unpacking w64codecs (from .../w64codecs_20061203-0medibuntu2_amd64.deb) ...
Setting up w64codecs (20061203-0medibuntu2) ...

---

### Post by xc3RnbFO8P on 2008-02-26
Check if you got **libstdc++5** installed (Synaptic Package Manager)

---

### Post by spamalot on 2008-02-26
Thanks.

No, libstdc++5 is not installed according to synaptic...

---

### Post by xc3RnbFO8P on 2008-02-26
Install libstdc++5
If it dont work you could try to install this plugin for Firefox.

sudo apt-get install mozilla-helix-player

---

### Post by spamalot on 2008-02-26
Thanks.

installing libstdc5++ does not solve the problem. e.g. 

[http://click.real.com/?pageid=radio.blues-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F7003528](http://click.real.com/?pageid=radio.blues-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F7003528)

opens a screen with Xine that stalls at 0 buffering and at the bottom left xine-plugin : no demuxer pluffing

Also, $ sudo apt-get install mozilla-helix-player
[sudo] password for er:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-helix-player\

---

### Post by spamalot on 2008-03-02
hi All, any more advice on this?

---

### Post by miwaypet on 2008-03-02
When this has happened to me I go to synaptic package manager and type in:

demuxing plugin.

It then shows me a couple of gstreamer apps. I check to install them and everything works fine after that.

Hope this helps.

---

### Post by spamalot on 2008-03-08
thanks, but still stuck with no demuxer plugin to handle stream e.g.

[http://click.real.com/?pageid=radio.alternative_punk-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F6964314](http://click.real.com/?pageid=radio.alternative_punk-ns&pageregion=main&href=http%3A%2F%2Fradio.real.com%2FmediaHurl%2F_%2Fstationid%2F6964314)

Search demuxer in synaptic manager yields

X libavformat1d
O libavformat-dev
X libxine1
O libxine-doc
X libxine1-plugins
O libxine-dev
X mpeg2dec
X xmms2-plugin-avformat

X: installed
O: not installed

Are there other plugins I should install? Any troubleshooting suggestion?

Thanks!

---

### Post by spamalot on 2008-03-10
if possible, could someone please search ""demuxer" in synaptic manager and tell me what he/she has intalled so i can figure out if something's missing in my configuration. Thank!

---

### Post by ron999 on 2008-03-10
Hi
There seems to be 4 installed in mine when I search for demuxer.

libavformat0d
libxine1
libxine1-ffmpeg
mpeg2dec

---

### Post by ron999 on 2008-03-10
Your link from post # plays for me if I enter from the keyboard:-

> mplayer rtsp://rx-wes-sea120.rbn.com/farm/pull/tx-rbn-sea006:2659/encoder/realone/realradio/open/live/1003895.rm

That's using mplayer.
Xine has never worked properly on my PC.
On the above link it shows a space between the zeroes on 1003895. There should be no space there.

---

### Post by spamalot on 2008-03-11
MPlayer with the GUI did not work, but from the terminal it does.

Thanks!

---


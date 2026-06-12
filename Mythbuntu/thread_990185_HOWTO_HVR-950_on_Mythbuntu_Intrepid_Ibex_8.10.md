---
title: "HOWTO: HVR-950 on Mythbuntu Intrepid Ibex 8.10"
date: 2008-11-22
forum: Mythbuntu
---

### Post by tgm4883 on 2008-11-22
HVR-950 on Intrepid

This is a guide adapted from a guide on the [MythTV wiki]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950").  Open a terminal and run these  (Note:  Each line in the code blocks is a separate command)

Setup a directory to work in
```
cd ~/
mkdir HVR950
cd HVR950
```

Get the zip file which ultimately contains the firmware and unzip it
```
wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
```

Install the kernel headers
```
sudo apt-get install linux-headers-generic
```

Copy the script needed to extract the firmware into your working directory and run it
```
cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
chmod +x extract_xc3028.pl
./extract_xc3028.pl
```

Copy the resulting firmware file into /lib/firmware: 
```
sudo cp xc3028-v27.fw /lib/firmware 
```

Reboot and you should now have a working tuner.  Continue through mythtv-setup

---

### Post by csuperk on 2008-11-24
hi
i tried to install the firmware as directed but, after running this command 

"cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
./extract_xc3028.pl"

i get "PERMISSION DENIED" i physically checked the file and it has a little lock beside it.
i'm new to linux and need a little help.

---

### Post by tgm4883 on 2008-11-24
> **csuperk said:**
> hi
i tried to install the firmware as directed but, after running this command 

"cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
./extract_xc3028.pl"

i get "PERMISSION DENIED" i physically checked the file and it has a little lock beside it.
i'm new to linux and need a little help.

Yea that does look a little confusing.  That is two commands.  Do 

```
cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
```

then

```
./extract_xc3028.pl
```

Let me know if that works for you.

---

### Post by csuperk on 2008-11-24
still the same, the exact command line i get after punching in "./extract_xc3028.pl" is 

bash: ./extract_xc3028.pl: Permission denied

also, i get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-misc-plugins libxcb-xv0 libxine1-bin libxine1-ffmpeg dkms
  libxcb-shape0 libxcb-shm0 libxine1-console
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

after punching in "sudo apt-get install linux-headers-generic"
i don't know if this matters.
Thanks

---

### Post by tgm4883 on 2008-11-24
> **csuperk said:**
> still the same, the exact command line i get after punching in "./extract_xc3028.pl" is 

bash: ./extract_xc3028.pl: Permission denied

also, i get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-misc-plugins libxcb-xv0 libxine1-bin libxine1-ffmpeg dkms
  libxcb-shape0 libxcb-shm0 libxine1-console
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

after punching in "sudo apt-get install linux-headers-generic"
i don't know if this matters.
Thanks

Nope, that means it's already installed.  Try this.

```
chmod +x extract_xc3028.pl
```
then
```
./extract_xc3028.pl
```

---

### Post by csuperk on 2008-11-24
yep that worked! 
mythbuntu scanned the channels and found them but it won't display any in the front end, just a black screen. no video, no sound.

but thanks for getting the firmware installed that is a big start.

Ubuntu is great!!, once this tuner is up and running i'm saying so long to microsoft.

---

### Post by tgm4883 on 2008-11-24
> **csuperk said:**
> yep that worked! 
mythbuntu scanned the channels and found them but it won't display any in the front end, just a black screen. no video, no sound.

but thanks for getting the firmware installed that is a big start.

Ubuntu is great!!, once this tuner is up and running i'm saying so long to microsoft.

Check your /var/log/mythtv/mythbackend.log  Sounds like you might have a problem with your storage directory

---

### Post by PushDustIn on 2008-11-26
Thanks for the instructions and the support.
I'm having a little bit of trouble though.... I followed these instructions, but Mythbuntu does not seem to recognize the TV tuner. I also tried following the [LunaPark]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") instructions but they are for Feisty Fawn so they don't seem to work in Ibex...

Thanks again!

---

### Post by tgm4883 on 2008-11-27
Did you add the card as a DVB card in mythtv-setup?  Were they any errors when following the above instructions?

---

### Post by PushDustIn on 2008-11-27
I tried adding the card as a DVB card in MythTV backend setup...however, the only card MythTV has listed is Auvitek Au8522 QAM Subtype: ATSC (DVB Device Number 0). It doesnt seem to pick up the HVR 950 even though Ubuntu recongizes it in the list of devices connected via USB... There was no problem in the above instructions~

---

### Post by tgm4883 on 2008-11-27
Interesting.  Whats the output of lsusb (with it plugged in)?

---

### Post by PushDustIn on 2008-11-27
Bus 003 Device 002: ID 2040:7200 Hauppauge

---

### Post by Casem on 2008-12-07
> **PushDustIn said:**
> I tried adding the card as a DVB card in MythTV backend setup...however, the only card MythTV has listed is Auvitek Au8522 QAM Subtype: ATSC (DVB Device Number 0). It doesnt seem to pick up the HVR 950 even though Ubuntu recongizes it in the list of devices connected via USB... There was no problem in the above instructions~

I am having the same issue trying to get this tuner to work on my combined backend/frontend. The only difference is that my tuner is a 950q if that matters.

---

### Post by chiok on 2008-12-13
I tried this on a fresh install with my Hauppauge WinTV-HVR-950Q Model 1191 and I also only saw the Auvitek AU8522 listed.

The lsusb item is:
Bus 001 Device 003: ID 2040:7200 Hauppauge

---

### Post by chuckroast00 on 2008-12-14
I am also seeing problems with Kaffeine:
All the above steps you suggest in the How2 seemed to work fine.
Where are we at with this?

DVB config Device Settings:

Auvitek AUB522 QAM/8VSB Frontend

lsusb -v :

Bus 002 Device 003: ID 2040:7200 Hauppauge 
Device Descriptor:                         
  bLength                18                
  bDescriptorType         1                
  bcdUSB               2.00                
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0        64                             
  idVendor           0x2040 Hauppauge                   
  idProduct          0x7200                             
  bcdDevice            0.05                             
  iManufacturer           1                             
  iProduct                2                             
  iSerial                10                             
  bNumConfigurations      1                             
  Configuration Descriptor:                             
    bLength                 9                           
    bDescriptorType         2                           
    wTotalLength          198                           
    bNumInterfaces          4                           
    bConfigurationValue     1                           
    iConfiguration          0                           
    bmAttributes         0x80                           
      (Bus Powered)                                     
    MaxPower              500mA                         
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       0                         
      bNumEndpoints           2                         
      bInterfaceClass       255 Vendor Specific Class   
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0                         
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x81  EP 1 IN              
        bmAttributes            3                       
          Transfer Type            Interrupt            
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0000  1x 0 bytes           
        bInterval              16                       
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x82  EP 2 IN              
        bmAttributes            1                       
          Transfer Type            Isochronous          
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0000  1x 0 bytes           
        bInterval               1                       
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       1                         
      bNumEndpoints           2                         
      bInterfaceClass       255 Vendor Specific Class   
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0                         
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x81  EP 1 IN              
        bmAttributes            3                       
          Transfer Type            Interrupt            
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0002  1x 2 bytes           
        bInterval              16                       
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x82  EP 2 IN              
        bmAttributes            1                       
          Transfer Type            Isochronous          
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0300  1x 768 bytes         
        bInterval               1                       
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        0                         
      bAlternateSetting       2                         
      bNumEndpoints           2                         
      bInterfaceClass       255 Vendor Specific Class   
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0                         
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x81  EP 1 IN              
        bmAttributes            3                       
          Transfer Type            Interrupt            
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x0002  1x 2 bytes           
        bInterval              16                       
      Endpoint Descriptor:                              
        bLength                 7                       
        bDescriptorType         5                       
        bEndpointAddress     0x82  EP 2 IN              
        bmAttributes            1                       
          Transfer Type            Isochronous          
          Synch Type               None                 
          Usage Type               Data                 
        wMaxPacketSize     0x03fc  1x 1020 bytes        
        bInterval               1                       
    Interface Descriptor:                               
      bLength                 9                         
      bDescriptorType         4                         
      bInterfaceNumber        1                         
      bAlternateSetting       0                         
      bNumEndpoints           0                         
      bInterfaceClass         1 Audio                   
      bInterfaceSubClass      1 Control Device          
      bInterfaceProtocol      0                         
      iInterface             11                         
      AudioControl Interface Descriptor:                
        bLength                 9                       
        bDescriptorType        36                       
        bDescriptorSubtype      1 (HEADER)              
        bcdADC               1.00                       
        wTotalLength           38                       
        bInCollection           1                       
        baInterfaceNr( 0)       2                       
      AudioControl Interface Descriptor:                
        bLength                12                       
        bDescriptorType        36                       
        bDescriptorSubtype      2 (INPUT_TERMINAL)      
        bTerminalID             1                       
        wTerminalType      0x0602 Digital Audio Interface
        bAssocTerminal          0                        
        bNrChannels             2                        
        wChannelConfig     0x0003                        
          Left Front (L)                                 
          Right Front (R)                                
        iChannelNames           0                        
        iTerminal               0                        
      AudioControl Interface Descriptor:                 
        bLength                 9                        
        bDescriptorType        36                        
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)      
        bTerminalID             2                        
        wTerminalType      0x0101 USB Streaming          
        bAssocTerminal          0                        
        bSourceID               3                        
        iTerminal               0                        
      AudioControl Interface Descriptor:                 
        bLength                 8                        
        bDescriptorType        36                        
        bDescriptorSubtype      6 (FEATURE_UNIT)         
        bUnitID                 3                        
        bSourceID               1                        
        bControlSize            1                        
        bmaControls( 0)      0x01                        
          Mute                                           
        iFeature                0                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        2                          
      bAlternateSetting       0                          
      bNumEndpoints           1                          
      bInterfaceClass         1 Audio                    
      bInterfaceSubClass      2 Streaming                
      bInterfaceProtocol      0                          
      iInterface             11                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x84  EP 4 IN               
        bmAttributes            5                        
          Transfer Type            Isochronous           
          Synch Type               Asynchronous          
          Usage Type               Data                  
        wMaxPacketSize     0x0000  1x 0 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        2                          
      bAlternateSetting       1                          
      bNumEndpoints           1                          
      bInterfaceClass         1 Audio                    
      bInterfaceSubClass      2 Streaming                
      bInterfaceProtocol      0                          
      iInterface             11                          
      AudioStreaming Interface Descriptor:               
        bLength                 7                        
        bDescriptorType        36                        
        bDescriptorSubtype      1 (AS_GENERAL)           
        bTerminalLink           2                        
        bDelay                  1 frames                 
        wFormatTag              1 PCM                    
      AudioStreaming Interface Descriptor:               
        bLength                11                        
        bDescriptorType        36                        
        bDescriptorSubtype      2 (FORMAT_TYPE)          
        bFormatType             1 (FORMAT_TYPE_I)        
        bNrChannels             2                        
        bSubframeSize           2                        
        bBitResolution         16                        
        bSamFreqType            1 Discrete               
        tSamFreq[ 0]        48000                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x84  EP 4 IN               
        bmAttributes            5                        
          Transfer Type            Isochronous           
          Synch Type               Asynchronous          
          Usage Type               Data                  
        wMaxPacketSize     0x0100  1x 256 bytes          
        bInterval               1                        
        AudioControl Endpoint Descriptor:                
          bLength                 7                      
          bDescriptorType        37                      
          bDescriptorSubtype      1 (EP_GENERAL)         
          bmAttributes         0x00                      
          bLockDelayUnits         0 Undefined            
          wLockDelay              0 Undefined            
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        3                          
      bAlternateSetting       0                          
      bNumEndpoints           1                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            2                        
          Transfer Type            Bulk                  
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0040  1x 64 bytes           
        bInterval               0                        
can't get device qualifier: Operation not permitted      
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

uname -a:
Linux desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by tgm4883 on 2008-12-15
I must admit that I didn't think it would be this difficult.  Admittedly, I only adapted these instructions from the mythtv wiki for 8.10 and only tested it in xine.  A quick google shows that the HVR-950q uses the Auvitek AU8522 ATSC/QAM/NTSC demodulator in it (and some reports show that the hvr-950 box actually contains a hvr-950q, although mine did not).  

Has anyone actually tried selecting Auvitek in mythtv-setup?

---

### Post by Casem on 2008-12-19
> **tgm4883 said:**
> Has anyone actually tried selecting Auvitek in mythtv-setup?

I tried selecting the Auvitek, but during channel scan it would time out on every channel.

---

### Post by awells527 on 2008-12-27
Hi, thanks for posting this tutorial.  I have gotten the card recognized correctly, but it doesn't entirely work yet.  I can find channels, but when I try to watch live TV, I only see a blue screen, but hear sound.  When I record a show, I can see the video in the preview before I select the show in MythTV, but when I view the recording, it's a blue screen with sound again.  What can I do to get the picture working?

---

### Post by skystiger on 2009-01-03
Hi, I know this post is for the 950, but I have a 900 and am sure it must be the same! My problem is that the firmware works, no problem, but it is still not creating the DVB directory and myth setup still cant get the DVB information from my card! any ideas?? Thanx

---

### Post by Chronon on 2009-01-09
I recently upgraded to Intrepid and was able to view my HVR-950 through xine.  I managed to install MythTV and watch some shows with that and everything seemed to be working fine.  Unfortunately, I rebooted since then and now it does not get recognized.  If I run the mythtv setup again (for the backend) it does not recognize any DVB cards as being attached.  It does list the HVR-950 as a valid choice as an analog tuner, however.  

Strange.

---

### Post by skystiger on 2009-01-09
Thats exactly what is happening to mine, going to try and install a vanilla kernel tonight and install v4l-dvb, and see if that fixes the problem, if anyone finds a better solution let me know!!

---

### Post by novellahub on 2009-01-09
You guys might want to try the instructions on the Knoppmyth Wiki for the HVR-950:

[http://www.knoppmythwiki.org/index.php?page=HVR950HowTo](http://www.knoppmythwiki.org/index.php?page=HVR950HowTo)

---

### Post by Chronon on 2009-01-09
Now I boot again and it works once more.  I haven't made any changes.

---

### Post by sam1965 on 2009-01-24
Has anyone gotten any further on this?

I can view analog channels.

Digital channels are located when I scan, but I only get "snow" when I try to view.

I don't get audio in analog or digital.

Aanyone figured it out?

Thanks

Sam

---

### Post by vronp on 2009-01-25
You're a bit further along than I am.

I think I'm getting stuck on drivers or something.  Mythth-setup recognizes the HVR-950 in some areas but not as a DVB.  Should it?

Regardless, when I try to "Watch TV", the screen just blinks and goes back to the menu.

Tvtime works with the HVR-950 in analog mode.

I am missing a step somewhere.

> **sam1965 said:**
> Has anyone gotten any further on this?

I can view analog channels.

Digital channels are located when I scan, but I only get "snow" when I try to view.

I don't get audio in analog or digital.

Aanyone figured it out?

Thanks

Sam

---

### Post by vronp on 2009-01-25
I'm getting a little further.  I'm somewhat of a mythtv noob so that is slowing me down.

I can watch analog TV but I don't get audio.

I don't see the HVR-950 listed as a DVB, only some DVB DTV device.

> **sam1965 said:**
> Has anyone gotten any further on this?

I can view analog channels.

Digital channels are located when I scan, but I only get "snow" when I try to view.

I don't get audio in analog or digital.

Aanyone figured it out?

Thanks

Sam

---

### Post by LinxPatrick on 2009-04-24
Sorry for posting this reply twice. I didn't realize that I had successfully posted this one before posting the second one.
 
 
 
I have followed these steps on a new installation of Jaunty. After completing the steps and then running modprobe em28xx or modprobe em28xx-dvb, the command returns no message. More importantly, it doesn't return with a FATAL error message.
 
I then installed Mythbuntu and it worked (except for suspend).

---

### Post by LinxPatrick on 2009-04-24
I have performed the steps on a new install of Jaunty. I ran modprobe on em28xx and em28xx-dvb. In both cases, no message was returned to the terminal window. The good news is that before running the steps a FATAL error message was returned.
 
I subsequently installed Mythbuntu and it worked. On the down side, I cannot suspend the machine with Mythbuntu installed.

---

### Post by glenn3451 on 2009-05-06
any updates on the sound problem? i have picture but no sound...

---

### Post by Chronon on 2009-05-12
In Jaunty I can watch TV using xine, but MythTV always just blanks the screen and returns me to the main menu whenever I select Watch TV.  I reinstalled MythTV and it was able to detect my card and successfully scan for channels, but the front end doesn't let me watch them.  (I did remember to restart the backend.)

UPDATE: I was having good success watching TV in Jaunty using Kaffeine.  After upgrading to 32-bit version of 9.10 I also had success using the newer version (KDE4) of Kaffeine to watch TV using the HVR-950.  I later installed a 64-bit version of 9.10 and haven't had any success watching TV since then.  I'll raise this elsewhere as it's kind of off-topic for this discussion.

---

### Post by Chamillo on 2010-01-16
> **tgm4883 said:**
> Yea that does look a little confusing.  That is two commands.  Do 

```
cp /usr/src/linux-headers-`uname -r`/Documentation/video4linux/extract_xc3028.pl ~/HVR950
```then

```
./extract_xc3028.pl
```Let me know if that works for you.

I'm running karmic and I have the HVR-950. I followed the instructions up to this point and everything seemed to go well until I ran

 ./extract_xc3028.pl

I get the error:

No such file or directory

What did I do wrong? How can I get the file? I will greatly appreciate some help with this.

---


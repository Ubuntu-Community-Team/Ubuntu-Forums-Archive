---
title: "MCE USB IR Blaster Not Working"
date: 2008-07-04
forum: Mythbuntu
---

### Post by Tim L on 2008-07-04
I am new to Linux and Mythbuntu – I can get everything working except for the IR Blaster to change channels on the satellite box. I am using a MCEUSB remote; the IR Blaster connects to the receiving box on the USB wire; the LED does not flash when the remote is pressed to change channels, although I can get it to flash by entering code in the Terminal.

I am using a combined front and back end, with a standard installation. I am sure my remote is a MCEUSB type <I have looked on the web and compared pictures>. I select “Windows Media Centrer New Version” and for the IR transmitter I selected “Microsoft Windows Media Centre (usb): sky”. 

I go through the installation and setup making minor changes. When setting up the video the computer does report “Probed infor: Hauppauge WinTV PVR-150 [ivtv]”. The satellite receiver is connected to the composite input on the video card. 

After Re-Boot I can use the remote to select TV and can see the programme from the Sky box correctly. Replay works along with other commands from the remote. 

When the change channel button is pressed on the remote about the bottom one third of the screen goes blue with the time and the channel number which changes each time I press the channel change button both up and down or when I enter numbers. I have used a digital camera to make sure I am not missing the inferred signal.  

In the terminal entering “irw” and pressing the buttons on the remote gives all the correct key press information.

I then very carefully followed the information in MythTV External Channel Changer, [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer). I have tried both methods to set up the IR Transmitter.  Still it does not work. 

I changed line five to $remote_name = “MCEUSB”

$ irsend SEND_ONCE MCEUSB ChanUp does work with the LED flashing.

Please can anyone help? I have completely reinstalled three times in case I have made a mistake, but  it is the same each time. I had thought the installation of the MCE remote was automated?

---

### Post by DutchLoki on 2008-07-04
> **Tim L said:**
> I am new to Linux and Mythbuntu – I can get everything working except for the IR Blaster to change channels on the satellite box. I am using a MCEUSB remote; the IR Blaster connects to the receiving box on the USB wire; the LED does not flash when the remote is pressed to change channels, although I can get it to flash by entering code in the Terminal.

I am using a combined front and back end, with a standard installation. I am sure my remote is a MCEUSB type <I have looked on the web and compared pictures>. I select “Windows Media Centrer New Version” and for the IR transmitter I selected “Microsoft Windows Media Centre (usb): sky”. 

I go through the installation and setup making minor changes. When setting up the video the computer does report “Probed infor: Hauppauge WinTV PVR-150 [ivtv]”. The satellite receiver is connected to the composite input on the video card. 

After Re-Boot I can use the remote to select TV and can see the programme from the Sky box correctly. Replay works along with other commands from the remote. 

When the change channel button is pressed on the remote about the bottom one third of the screen goes blue with the time and the channel number which changes each time I press the channel change button both up and down or when I enter numbers. I have used a digital camera to make sure I am not missing the inferred signal.  

In the terminal entering “irw” and pressing the buttons on the remote gives all the correct key press information.

I then very carefully followed the information in MythTV External Channel Changer, [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer). I have tried both methods to set up the IR Transmitter.  Still it does not work. 

I changed line five to $remote_name = “MCEUSB”

$ irsend SEND_ONCE MCEUSB ChanUp does work with the LED flashing.

Please can anyone help? I have completely reinstalled three times in case I have made a mistake, but  it is the same each time. I had thought the installation of the MCE remote was automated?


The installation of the MCE remote should be fairly easy. for default usage it all works out of the box. 

But reading your post i see you want the IR blaster to control your sky box and you sticked one of the IR blaster on your satellite box to accomplish this? 

As I see it, you should do two things: 

1) configure MythTV to use the right kind of mce remote (It looks like this part done right)

2) configure mythTV to send the right signals trough the ir blasters to control your box. Because you say myth is not sending any signals, it looks like some control signals are not configured right. It seems this step needs you attention. Besides choosing a preconfigured ir blaster setup, its also possible to configure this manually. You could try this for one of the remote commands that are not working at the moment. 

About how to configure this manually you should check the MyhtTV wiki (sorry don't have time to look it up for you right now, some friends just walked in).

---

### Post by sikk on 2008-07-04
> **Tim L said:**
> I am new to Linux and Mythbuntu – I can get everything working except for the IR Blaster to change channels on the satellite box. I am using a MCEUSB remote; the IR Blaster connects to the receiving box on the USB wire; the LED does not flash when the remote is pressed to change channels, although I can get it to flash by entering code in the Terminal.

I am using a combined front and back end, with a standard installation. I am sure my remote is a MCEUSB type <I have looked on the web and compared pictures>. I select “Windows Media Centrer New Version” and for the IR transmitter I selected “Microsoft Windows Media Centre (usb): sky”. 

I go through the installation and setup making minor changes. When setting up the video the computer does report “Probed infor: Hauppauge WinTV PVR-150 [ivtv]”. The satellite receiver is connected to the composite input on the video card. 

After Re-Boot I can use the remote to select TV and can see the programme from the Sky box correctly. Replay works along with other commands from the remote. 

When the change channel button is pressed on the remote about the bottom one third of the screen goes blue with the time and the channel number which changes each time I press the channel change button both up and down or when I enter numbers. I have used a digital camera to make sure I am not missing the inferred signal.  

In the terminal entering “irw” and pressing the buttons on the remote gives all the correct key press information.

I then very carefully followed the information in MythTV External Channel Changer, [https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer). I have tried both methods to set up the IR Transmitter.  Still it does not work. 

I changed line five to $remote_name = “MCEUSB”

$ irsend SEND_ONCE MCEUSB ChanUp does work with the LED flashing.

Please can anyone help? I have completely reinstalled three times in case I have made a mistake, but  it is the same each time. I had thought the installation of the MCE remote was automated?

Hello, 

I run almost the exact same setup as you. Even down to the Sky STB (well it's actually a Foxtel STB here in Oz, a rebadged Sky).

```
REMOTE_NAME=sky
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.5
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select 
```

Can I assume your "change-channel-lirc.sh" looks like above?

Does your /etc/lirc/lircd.conf have a "sky" remote section that looks something a bit like this?

```
begin remote

  name          SKY
  flags         CONST_LENGTH|RAW_CODES
  eps           30
  aeps          100
  ptrail        0
  repeat        0     0
  gap           249692
#  gap          112269
  frequency     36000
  duty_cycle    50

  begin raw_codes

    name 0
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444

    name 1
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      888

    name 2
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 888 888
      444

    name 3
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 888 444
      444

    name 4
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 888 888 444 444
      444

    name 5
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 888 888 888

    name 6
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 888 444 444 888
      444

    name 7
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 888 444 444 444
      444

    name 8
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 888 888 444 444 444 444
      444

    name 9
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 888 888 444 444 888

    name RED
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 888 888 444 444 888 888

    name GREEN
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 888 888 444 444 444 444 888 444

    name YELLOW
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 888 888 444 444 444 444 444 444

    name BLUE
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 444 444 888 444 444 444 444 444 444
      444

    name TEXT
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 888 444 444 444 444 444 444 888 444 444
      444

    name BACKUP
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 888 444 444 444 444 444 444 444 444 888 444 444

    name HELP
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 888 444 444 444 444 444 444 444 444 444 444 888

    name CURSOR-LEFT
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 888 888 444 444 888 888 888 444

    name CURSOR-DOWN
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 888 888 444 444 888 444 444 888

    name CURSOR-RIGHT
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 888 888 444 444 888 888 444 444

    name CURSOR-UP
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 888 888 444 444 888 444 444 444 444 444

    name SELECT
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 888 888 444 444 444 444 888 444 444 444

    name CHANNEL-DOWN
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 888 888 444 444 444 444 444 444 888

    name CHANNEL-UP
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 888 888 444 444 444 444 444 444 444 444
      444

    name I
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 444 444 888 444 444 888 888 888 444 444

    name ONOFF
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 888 444 444 888 444 444
      444

    name TV
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 888 444 444 444 444 444 444 888 888 444 444 444

    name SKY
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 888 444 444 444 444 444 444 444 444 444 444 444 444
      444

    name TVGUIDE
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 444 444 888 444 444 888 444 444 888 444 444 444

    name BOXOFFICE
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 444 444 444 444 444 444 888 888

    name SERVICES
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 444 444 888 444 444 444 444 444 444 444 444 444 444 888
      444

    name INTERACTIVE
      2664 888 444 444 444 444 444 888 444 888 888 444 444 444 444 444
      444 444 444 444 444 444 444 444 444 444 444 444 444 444 444 444
      444 444 888 444 444 444 444 444 444 888 888 888 888

  end raw_codes

end remote
```

If so, what happens when you run 

```
change-channel-lirc.sh 100
```

from the command line?

Be aware that I found that the transmitter from the MCE USB needed to be EXTREMEELY close to the (PACE) STB I have to get any results, basically I needed to bluetak it to the receiver.

Good luck.

---

### Post by Tim L on 2008-07-05
Sikk

Yes my "change-channel-lirc.sh" looks almost like the one you posted. It took a long time to realise that REMOTE_NAME=sky was correct when logic says it should be REMOTE_NAME=MCEUSB. 

My &#8220;/etc/lirc/lircd.conf&#8221; looks nothing like yours &#8211; it is like this &#8211; I am only including part:

#The configuration has been automatically generated ...

#Configuration for the Windows Media Center Remotes (new version Philips et al) remote: include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the Microsoft Windows Media Centre V2 (usb) : Sky Satellite Receiver transmitter:
include /usr/share/lirc/transmitters/sky/general/conf


When I run $ change-channel-lirc.sh 100 in the terminal the LED flashes correctly.

No matter  what I try the IR does nothing when trying to change the channel with the remote.

Thanks

---

### Post by impossibilechecisiaquesto on 2008-09-21
Same Problem. My script work fine in the shell, but inside mythtv it doesn't nothing, no flash.
Any ideas?

---

### Post by rogers21 on 2008-10-23
> **Tim L said:**
> Sikk

Yes my "change-channel-lirc.sh" looks almost like the one you posted. It took a long time to realise that REMOTE_NAME=sky was correct when logic says it should be REMOTE_NAME=MCEUSB. 

My “/etc/lirc/lircd.conf” looks nothing like yours – it is like this – I am only including part:

#The configuration has been automatically generated ...

#Configuration for the Windows Media Center Remotes (new version Philips et al) remote: include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the Microsoft Windows Media Centre V2 (usb) : Sky Satellite Receiver transmitter:
include /usr/share/lirc/transmitters/sky/general/conf


When I run $ change-channel-lirc.sh 100 in the terminal the LED flashes correctly.

No matter  what I try the IR does nothing when trying to change the channel with the remote.

Thanks

Did you get a fix for this?

---


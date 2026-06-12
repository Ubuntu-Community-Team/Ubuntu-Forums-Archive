---
title: "Modem apparently not connecting"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Penbwlch on 2009-12-06
Hi, I am trying to help someone who has a problem laptop. Initially, in Windows, the modem was not working. It soon became apparent that the problem was a corrupted Windows and the modem was fine. I suggested trying Ubuntu and am now trying to get it to work for him. Please bear with me as this is my first venture with Linux.

I have managed to find a driver for the modem (Zoom USB dial up, model 3095) and got it installed. I have set it up so that it dials the ISP and (going by the sound) seems to be connected. However, Firefox tells me otherwise and the data light on the modem does not light.

I have double checked the number and customer details and they are correct. I have even tried another dial-up provider (a free one) and the same happens there.

Can anyone please suggest anything that could cause this problem. I am happy that the modem works correctly (I've even tried a second one just in case) and I am happy that the ISP connection works from other computers.

---

### Post by _duncan_ on 2009-12-07
check if firefox is starting in offline mode. It might also help if you can post the log messages of the dialer you are using.

---

### Post by Penbwlch on 2009-12-07
> **_duncan_ said:**
> check if firefox is starting in offline mode. It might also help if you can post the log messages of the dialer you are using.

Yes, I do have Firefox starting in online mode. I have googled for log messages and checked this machine but there don't appear to be any. I presume there is a setting to start the logging but cannot find it. Could someone advise, please?

---

### Post by _duncan_ on 2009-12-07
1. What version of Ubuntu are you running?
2. Which dialer program are you using to connect to the ISP? (wvdial? pppconfig? gnome-ppp?)

---

### Post by Penbwlch on 2009-12-07
1. 9.04
2. System/Administration/Network

---

### Post by _duncan_ on 2009-12-07
System/Admin/Network is a little flaky as a dialer.

For fresh installs, I recommend using the terminal-based dialer pppconfig to achieve initial connection, then download the GUI dialer gnome-ppp for subsequent connections.

Open a terminal (Applications > Accessories > Terminal) and enter the following command:
```
sudo pppconfig
```

You will be prompted for connection info to your ISP. Note the following:

1. The mouse doesn't function on this screen. You will have to use keyboard to navigate. (Tab key to move, space key to select, etc.) The instructions are on the screen, so please take the time to read them thoroughly.

2. Make sure to choose dynamic IP.

3. See if the program can audotect the modem. If not, you will have to enter the device manually. Not sure if you know where the modem is located. For serial-port connected modems the modem is /dev/ttyS0 or /dev/ttyS1. Maybe you can look at where System > Admin > Network is pointed to since it seems to autodetect the modem. Post back if you have problems with this step.

4. Leave the name as 'provider'.

-----------------------

After you're through with the configuration, suggest you enter the following in the terminal to make sure your user ID has all the necessary privileges:

```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```

where [COLOR="Blue"]userID[/COLOR] is your actual user ID.

logout and login for the changes to take effect.

------------------------

Assuming the above steps are trouble-free. To connect, type this in the terminal:

```
pon
```

To disconnect```
poff
```

To get connection log in case there is trouble ```
plog
```

---


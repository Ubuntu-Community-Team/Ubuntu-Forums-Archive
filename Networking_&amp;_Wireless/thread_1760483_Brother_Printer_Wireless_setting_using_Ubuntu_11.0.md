---
title: "Brother Printer Wireless setting using Ubuntu 11.04"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by HoffmanP on 2011-05-17
Hello Guys,

I just succesfully installed my printer driver. My rpinter is Brother MFC 255 CW. It works fine when I connected thorugh USB cable. 

Then I tried to figure out how to connect using the wireless connection from the printer. Somehow ubuntu can't detect the printer signal.

This is so far the way what I did to try getting the printer connect to my laptop:
- System setting
- Printer
- Add Printer
- Network Printer
- Appsocket/HP Jet Direct, then set the host with the IP address that the printer provided and port number: 9100
- selecting the drive / installation
- after the additional installation finish I tried to print test page and nothing happen.:confused:

Is there any other way to figure out how to make the wireless working? Or maybe I did something wrong on the process...Please guys help me out......

---

### Post by Bucky Ball on 2011-05-17
You need to set it up via the cable first. Print the Printer Settings and check the IP address it has assigned itself (probably via APIPA), then open System>Admin>Printing and add a new printer (LPD/LPR),

This is the important bit: For host put in the IP address you got from the printer settings print out. For queue you need to put:

> binary_1Your printer should be installed on the network (open a terminal and try pinging the printer's IP). On my Brother printer (HL-2270DW) there is a hole on the back near the  network cable slot where you need to insert the end of a pen for ***less*** than two seconds to switch the wireless on (off by default). Do that. Now open Firefox and in the address bar type:

> [http://xxx.xxx.xxx.xxx]("http://xxx.xxx.xxx.xxx/")... where xxx.xxx.xxx.xxx is the IP address of your printer. This should take you to the printer configuration. 

From here you can give the machine a static IP for both wired and wireless. For wireless you are going to need the details of your wireless router; ESSID, security type, gateway, subnet mask, etc. You don't need 9100 or anything else for wireless. Once the printer is communicating with your router if you open System>Admin>Printing it should be there, click it and it's a piece of cake to set up from there.

You should be up and running in no time. ;)

Take note; by default the printer will only use cable or wireless, not both at the same time, but you will find you can change this to 'Auto Detect' in the printer configuration in Firefox so you can use both (handy in some situations I guess). Let us know how you went.

---

### Post by HoffmanP on 2011-05-17
bucky_ball: I did what u told me to do....still the computer can't connect to the printer....I put the ip address on firefox and it can open the printer admin....when I tried to test print the status on the printer state is 'processing - connecting to printer....' I waited and it's been couple of minute and nothing going on...:confused:

---

### Post by Bucky Ball on 2011-05-17
A/ Are you plugged in with a cable and it prints that way?
B/ If you are attempting to print with wireless you need to switch it on in the hole at the back with a pen.
C/ To get the printer settings you probably need to push a button on the machine three or five times. Try and do that from the machine and not the config interface. 

For wireless to connect you need to assign a *different *IP to the wired connection in the printer config and give it the appropriate details to join the wireless network. 

I'm not clear on whether you are attempting to print from the cable connection or the wireless at this point. Did you get the printer settings? Where did you find the printer's IP?

---

### Post by HoffmanP on 2011-05-17
A/ Are you plugged in with a cable and it prints that way?
"When I am using the USB cable the printer works fine. But now what I am trying to do is using the printer through wireless connection."

B/ If you are attempting to print with wireless you need to switch it on in the hole at the back with a pen.
"In my printer there is no switch like you described above. I have to go to the printer menu instead to get the wireless on."

C/ To get the printer settings you probably need to push a button on the machine three or five times. Try and do that from the machine and not the config interface.
"Yes I use the setting you look for the printer IP address" 

For wireless to connect you need to assign a *different *IP to the wired connection in the printer config and give it the appropriate details to join the wireless network.
"So you are saying that I have to change the IP address on the printer, so it differ from the wireless connection?" 

I'm not clear on whether you are attempting to print from the cable connection or the wireless at this point. Did you get the printer settings? Where did you find the printer's IP?
"I am trying to print through the wireless connection. The cable connection works just fine. I got the printer IP from the printer 'network' menu. There is a TCP/IP menu then press ok the IP address shown."

I tried this way:
go to:
- Systems Setting
- Printing
- Add new printer
- Network printer choose LPD/LPR
- I input the hostname/ IP address ( i got this number from the Brother Printer Network Menu), set queue binary_1
- Choose printer driver to install ( I found my printer type on the list "MFC 255CW CUPS"
- After the installation, I can see the icon on the printing menu. But then when i tried to test print nothing going on "again". :sad:

---

### Post by Bucky Ball on 2011-05-17
When I say cable connection I mean network cable, *not *USB. You need to get up on wired then open the printer config with the IP address in Firefox. In there you need to configure wireless with the correct details to match your router. Once you have done so unplug the cable from the printer (unless you have set the printer to AUTO so it recognises either but for the purposes of this unplug it).

Print the wlan settings (3 presses on the button for me) and make sure the printer is set with the wireless details you entered in the config interface. If not there is something amiss.

If so, make sure the wireless on your printer is switched on, then System>Admin>Printing>Add Printer. WAIT! It takes awhile before all available network printers are recognised and displayed. If you have things right your wireless printer should appear as Brother (BRWxxxxxxx) or something like that. 

Hope that helps. ;)

PS: If you are printing from USB you have the printer driver installed. There is no need to install anything for wireless in that case; it should just happen when you get it right.

---

### Post by HoffmanP on 2011-05-18
> **Bucky Ball said:**
> When I say cable connection I mean network cable, *not *USB. You need to get up on wired then open the printer config with the IP address in Firefox. In there you need to configure wireless with the correct details to match your router. Once you have done so unplug the cable from the printer (unless you have set the printer to AUTO so it recognises either but for the purposes of this unplug it).

Print the wlan settings (3 presses on the button for me) and make sure the printer is set with the wireless details you entered in the config interface. If not there is something amiss.

If so, make sure the wireless on your printer is switched on, then System>Admin>Printing>Add Printer. WAIT! It takes awhile before all available network printers are recognised and displayed. If you have things right your wireless printer should appear as Brother (BRWxxxxxxx) or something like that. 

Hope that helps. ;)

PS: If you are printing from USB you have the printer driver installed. There is no need to install anything for wireless in that case; it should just happen when you get it right.

Mmmmm I dont use any router. I thought that I could use the network  wireless from the printer. Because the printer already has Network wireless. On the printer menu it has the Network menu which provided the IP address, MAC address etc.... I dont think I need external router anymore.
 
On the Windows XP I dont use any router and it was  so easy to setup. Just turn on the wireless from the computer and printer. From the computer you just need to scan the available Wireless Network connect it and you are done.

From Ubuntu, how do I scan the available wireless network? :confused:

---

### Post by Bucky Ball on 2011-05-18
If it is up and running as you describe in Windows, you should be able to go:

> System>Admin>Printing>Add Printer. WAIT! It takes awhile before  all available network printers are recognised and displayed. If you  have things right your wireless printer should appear as Brother  (BRWxxxxxxx) or something like that. From my last post. You don't need to install anything or do much if the printer is up wirelessly. But you do need to add printer and wait for the network printers (and all available printers) to show in the left pane of 'Add Printer' GUI. 

If the machine is working with Ubuntu via USB then you have installed the drivers already and any further installation of things should be unnecessary.

---

### Post by HoffmanP on 2011-05-18
Holy Cow this is the first time in my life that I encountered such great deal of stress just installing a wireless printer.....but not it solved.

Anyway just for documentation purpose I will describe how I did this connection to work which also I think this can be use for other wireless network printer:

I installed the printer driver. Use the instruction from this thread:
[http://ubuntuforums.org/showthread.php?t=590793&highlight=installing+printer+brothers](http://ubuntuforums.org/showthread.php?t=590793&highlight=installing+printer+brothers)
I did this first so that I know it driver works.
 Now you have to configure the wireless network setting.

setting up the Network Wireless Printer to connet to Ubuntu:
- Check your printer and get it to print the "Network Configuration" information.
- Go to Network Manager - Edit Connection
- Fill up the information:
SSID : ( you can see the network name from the network configuration that you print"
Mode : Ad hoc
Band : Automatic
BSSID : "Leave it blank"
Device MAC address " "leave it blank"
Cloned MAC address: "Leave it blank"
MTU: Automatic

Then got to IP4v Setting:
You change the method to "Manual" setting. Then fill up the IP address, Subnet Mask, and Gateway value from the Network Configuration print out. 
Leave the DNS server and Seacrh Domain blank.

Click save.

By now you should be able to connect your printer wireless network. To check on this you go to terminal then type: ping "ip address"
If it pings goes on and on then you are connected.

Last part you need to configure your printer setting
Go to firefox and type : [http://localhost:631](http://localhost:631)
Click to Printer - Modify Printer
By now you should see "discovered network printer" click on that and continue follow all the command.
when you are done try to print a test page.....when you can print that you are all set

4 days just to figure out how to connect....any way it connected, I can enjoy more of this operating system.....:popcorn:

Hope this helps...

PS: I am a newbie just installed the Ubuntu 11.04 natty last week...and this the first time I use unix...love Mr Google and this forums....a lot of information....

---

### Post by Bucky Ball on 2011-05-19
All sound good, glad you got it working. If you print the printer settings (or just the wlan page) does it show your wireless configuration on the printer matches what you have in Network Manager?

---

### Post by HoffmanP on 2011-05-19
> **Bucky Ball said:**
> All sound good, glad you got it working. If you print the printer settings (or just the wlan page) does it show your wireless configuration on the printer matches what you have in Network Manager?

Well in my case, I wouldn't say it doesn't matche but it just blank and you have to fill up the value from the Printer Wireless Network print out. That is why the printer wireless didn't connect to my laptop. At first, I only filled up the IP address and still not working. Then I tried to fill up the IP4v setting tab voila it works...

But now the scanner isn't working :confused: never ending story yah....

When Xsane tried to find the scanner a window come up saying "Failed to open bla bla bla bal..."

---

### Post by Bucky Ball on 2011-05-19
I would post a new thread regarding your scanner problem with a suitable title. Put a link to it here if you like.

Good luck. ;)

---

### Post by Jemy08 on 2013-02-27
Thanx HoffmanP. 
Even though your thread is 2 years old, it helped me solving a problem with my printer. I've installed my printer half a year ago and everything went fine.  Suddenly my ubuntu can't connect to the printer anymore. 
Anyway, you helped me solve the problem. 
Just one thing: after setting up the network using the network configuration from the printer,  and after modifying the printer in cups admin, I had to change the connection URI and integrate the printer's IP. CUPS used something that was blocked by the firewall.
Cheers

---


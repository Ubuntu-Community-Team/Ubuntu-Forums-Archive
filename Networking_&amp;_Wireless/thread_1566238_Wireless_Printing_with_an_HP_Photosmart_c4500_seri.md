---
title: "Wireless Printing with an HP Photosmart c4500 series"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by jmwilli25 on 2010-09-02
I finally got around to setting up my HP Photosmart c4580 AIO printer today to print wirelessly so that I don't have to be tethered to it with a USB. I found there are many different ways of doing this, each with limited success. So I took a crack at it and this is how I got it to work. (Just an FYI, I don't think that it matters but I am running Ubuntu 10.04 64bit.) Note: I have put in screen shots of the important steps. Also, I have linked at the bottom all the relevant shots.

In a terminal type
```
hpsetup
```

After pushing enter a GUI will pop open call "HP Device Manager - Setup". There are four radio buttons, I selected the "Wireless/802.11 (requires a temporary USB connection and is only available for select devices)" one and then clicked Next.

Clicking Next opens a new window for Wifi Configuration. Read what it says (Which is; after configuration setup will continue, this configuration may not work, and connect your printer to your computer by a USB cable!)

Now click "Next".
Assuming you haven't forgotten to plug your printer into your computer (and turn it on) you will get a "Discovered Wireless Capable Devices" list with something on it. If you do not have anything listed under "Model" and "Device URI" check all your connections and the power to your printer and click refresh. If still nothing I am sorry but this setup has failed you, but if you are lucky and something shows up, click on it and then click next.

You have to have wireless internet to continue. The step you are on now has you select your wireless internet connection. Find your's and click next.

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot4.png[/IMG]

Now in the next screen you have to enter in your password for your wireless internet, then push connect. Once you connect you have now just given me access to your online banking and I am withdrawing money as you read this! I'm **probably** just kidding! I just wanted to make sure I haven't lost you yet. But you do want to enter your password and push enter.

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot6.png[/IMG]

After you push connect you should get a little 'progress' screen.

After that is done loading you will see a screen that looks like

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot8.png[/IMG]

Now on a piece of paper or something else, write down your hostname and your IP address. After you have done that **unplug the USB from your computer** and click finish. Now what happens next, I could not explain. But you remember earlier the wizard said that setup would continue after configuration? Yeah well it didn't for me. And here is what it looked like. 

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot9.png[/IMG]

Notice no printers available to select, and even in the terminal it shows an error. Either way, we have the information that we need to finish things up outside of this 'hpsetup' wizard. So just click cancel, close the terminal, and go back to the desktop. 
Now on your desktop go to System>Administration>Printing That will open a window that shows your current printer profiles. Click the add button to get a screen that looks like this

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot11.png[/IMG]

Click the plus sign **+** next to "Network Printer" then click on "Find Network Printer". Now on the right half of that window there is a text box labeled "host:", enter the IP address that you copied down earlier and click the button that says "Find". Once clicking "Find" , one of two things will happen; (1)It will recognize it right away, locate the driver and take you to this screen, after clicking "forward".

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot12.png[/IMG]

or (2) It will take you to a screen showing the host name and the port number. If that happens, no big deal, just click "forward" to get the above screen. Or (3) It will not recognize the IP address that you entered. If this is the case, type in the host name you copied down earlier and click find, then click "forward" to get to the above screen. Or (4) It will not be able to locate a suitable driver. If this last scenario plays out for you then I am sorry but I don't know what to do. So lets just hope that doesn't happen.

Alright now that you are on the above screen. Type in a name that you would like your computer to call your printer.

[IMG]http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot13.png[/IMG]

Then click "Apply". Once you click "Apply" that window will close and it will take you back to your printer list. You should notice a new printer in your lineup. Also, it is asking you if you would like to print a test page. Before you pick one, double check that your USB cable is no longer plugged in to your computer from the printer. Now, clicked "No" or "Yes". I chose "No" because test printing takes up a lot of ink. Instead of the test page I just went to my gmail and printed an e-mail. And guess what?! It worked! I hope that you have as much success as I have had.

Here are the links to all the screen shots
1. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot.png)
2. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot1.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot1.png)
3. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot2.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot2.png)
4. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot3.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot3.png)
5. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot4.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot4.png)
6. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot6.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot6.png)
7. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot7.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot7.png)
8. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot8.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot8.png)
9. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot9.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot9.png)
10. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot10.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot10.png)
11. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot11.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot11.png)
12. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot12.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot12.png)
13. [http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot13.png](http://i866.photobucket.com/albums/ab221/jmwilli25/Screenshot13.png)

---

### Post by jmwilli25 on 2010-11-27
Any success/fail stories?

---

### Post by cybergnome on 2010-11-28
There is one important point that you have overlooked.  When the built-in print server is configured to use DHCP, the lease can expire and the IP may change.  The workstations won't be updated, and will still use the old IP with no success.  For that reason, the printer should be configured with a static IP, rather than DHCP.

This way there will be no changes to cause and interruption and the need to reconfigure.

---

### Post by simonthd on 2011-04-15
Thank you very much !!! Success here :) HP Photosmart 209a

---

### Post by rye n on 2011-09-19
success!

---

### Post by bobstead on 2012-02-22
Great help! I'd sp[ent hours since upgrading to 11.10 trying to get the printer workingf again & this finally solved it.  Thanks

---

### Post by craigward2000 on 2012-06-03
I did this and it appears to work at first but the problem is that the router allocated different IP addresses when the system is powered down.  Like a previous poster said the solution is to allocate a fixed Ip address. 

Info to do this is in here: [http://www.hp.com/global/us/en/wireless/faq.html](http://www.hp.com/global/us/en/wireless/faq.html)

Basically you print a network test page at your printer. Then open a web browser and type in the printer ip address direct into the browser address bar. This will let you talk to the printer directly. What I did was to keep all the address's the same as the test sheet but change the last digit on the IP address to 150. Note that once you apply the settings the webpage will not reload as the ip address has changed and you must enter the new ip address into the brower address bar.

---


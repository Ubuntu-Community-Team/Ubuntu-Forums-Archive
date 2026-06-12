---
title: "Compaq Mini and Broadcom 43xx"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2011-04-06
Hi all.

Am running 11.04, probably upgraded by daily updates to the latest Beta version by now on the above machine and all is peachy! 

That is whilst the machine is connected to the mains. On battery power network/internet performance is diabolical!

Can somebody let me know the commands to check the card to see if power saving's turned on, and if it is to turn it off!! Unless there's a graphical way that I'm missing.....

Thanks in advance everyone.

---

### Post by AlanR8 on 2011-04-07
Bumpity Bump Bump!!!!!

---

### Post by AlanR8 on 2011-04-08
Quick....before I go and sulk and think no one cares......:D

BUMP BUMP!!!!

Seriously...just done today's "Partial" updates and attached to the power, 800 + kbs download speed. On battery power, 50 kbs.

What can I do?

---

### Post by AlanR8 on 2011-04-09
Paranoia is beginning to set in now.....

BUMP BUMP BUMP

Battery network is dire/diabolical/unusable/slow/sh**e/poor

Mains network is cool/fast/swish/usable/quick/sh*t hot/great

---

### Post by AlanR8 on 2011-04-11
So again......

BUMP

---

### Post by AlanR8 on 2011-04-15
Many bumps later and I've found the answer myself.

The script to disable power saving on the Broadcom chipset is as follows:

> sudo iwconfig eth1 power off

Speeds are now around the 6942 kbps level rather than less than 1000 kbps.

Deep joy! Problem solved providing I manually type the above command after boot up.

So, how do I make an admin script run at start up without user intervention?

---

### Post by AlanR8 on 2011-04-16
Whilst there were no responses to my query, after quite a bit of research I've now answered the question I originally asked. I've also found a solution to automatically shut off power saving on my Broadcom wireless card when the machine logs in.

I KNOW other people must be having the same problem as I was having on my Compaq Mini Netbook equipped with a Broadcom network card. On battery power, network and internet performance was DIRE but on mains power all was well. 

Here's what I did so you don't have to go through the pain of figuring it out yourself. I've marked the thread as Solved for quick internet searches in the future.

Enjoy and credit to to the various sources I found.

> To shut power saving off on a wireless network card

Very simply, the command is as follows:

sudo iwconfig eth1 power off

This will work but you will have to execute the command on every start up or log on to the system, so it can be automated as follows.

Create an executable script as follows:

Press Alt and F2  and in the “Run Application” box that opens type “gedit” without the quotes.

This opens the text editor called gedit in Ubuntu.

Type or copy this single line of code into the text file:

sudo iwconfig eth1 power off

Save the file with a name of your choice but give it the extension .sh

I saved my file in my Home Folder but as a hidden file so it won't get accidentally deleted as:

 .network_power_off.sh

(Note the . at the start of the file name that makes the file hidden in normal use).

Open Nautilus, your file manager, and from the “View Menu” select “Show Hidden Files”. Scroll down the list of folders then files and find your newly created file. 

Right click the file and from the resulting menu select “Properties” then the “Permissions” tab. 

Put a tick in the box beside “Allow executing file as a program” then click “Close”.

Next thing to do is to get the file to automatically run at start up.

Go to your main menu on the upper pane and follow the route:

Systems/Preferences/Startup Applications. In the box that opens click the “Add” button.

There are three items to edit here.

Name.

Give your new command a name. It can be anything, mine is “Network Power Save OFF”.

Command.

Mine is: gksu /home/alan/.network_power_off.sh

Note you could use the “Browse” button to find the file you created earlier.

Description.

Again anything you want and is not required by the system.

Click “Save” to save the command and reboot your machine.

On restarting, just after the log in screen, you will now have another box open asking for your Admin password to run the script you just created. Enter your password and the system will complete the log in process. 

I then check the script has worked by testing my Internet download speed. Running on battery with power saving on the download speeds are dire, usually around 800 kbps. On mains power, and with power saving off, download speeds approach the theoretical maximum I can expect from my current ISP, around 6700 kbps. I now get the higher speeds on battery power as well.

To get rid of the additional password box we need to complete a final step as follows. 

Press Alt and F2 again and this time enter or paste the following command into the dialogue box:

gksu gedit /etc/sudoers 

Click the “Run” button. Next you will be asked for your Administrator password to proceed with editing the file. Enter your password and the file /etc/sudoers will be open for editing.

Go to the bottom of the file and add the following line:

username ALL= NOPASSWD: scriptpath

This line needs editing to suit your username and where you saved the file. On my system the line looks like this:

alan ALL= NOPASSWD: /home/alan/.network_power_off.sh

Once the line is edited, save the changes, close the file and reboot.

This time you should NOT get the second password request just after the login screen! If you do, like I did, go back and check your edits. I found two spelling mistakes. Remember Linux is case sensitive!


---


---
title: "Network Manager not working in Ubuntu 8.04 for Inspiron 910"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by francopdx on 2009-05-06
I just wrote a very lengthy question detailing everything I've tried already to fix the problem, and when I hit the "submit" button, it cleared everything I typed and said the message had to be at least 1 character long.  The message was hundreds of characters long, and I can't re-type all of it right now, so here's the summary.

The Network Manager in my Mini 9 no longer loads, so I can't access wireless connections on my laptop.  It worked fine for the first two weeks, but after downloading system updates, it started to give me problems (occasionally not loading) and after 2 or 3 updates, it no longer loads at all, so I can't access any wireless connections.

I tried figuring out the problem myself, but after hours of reading official info and forums like this, nothing worked, so I've decided to ask my own question.

The first thing I tried was installing Wicd but my computer wouldn't let me.  It gave me the following error message after I hit Reload in the Synaptic Package Manager:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://apt.wicd.net/dists/hardy/Release](http://apt.wicd.net/dists/hardy/Release)  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead."


The next thing I tried was installing the KNetworkManager by using the Add/Remove Applications program, but it gave me this error message:

"Cannot install 'network-manager-kde'

This application conflicts with other installed software. To install 'network-manager-kde' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."


I even tried removing the orignal Network Manager through the Add/Remove program and then adding KNetworkManager, but that didn't work either.

Is there any way to fix this problem or should I just switch to Windows?  I thought Ubuntu would be a good system to try out, but if I can't connect to the internet with wireless, it just makes this laptop useless.

---

### Post by phantom3113 on 2009-05-06
The reason it's giving you those errors is because NM isn't working right. If you can manage to get a LAN connection to the router you use, I would suggest doing that and trying to get wicd again. I know how you feel, as I got sick of dealing with NM :) If you get wicd through synaptic, it should download the necessary files for wicd, and then carry out with the removal of NM and then the install of wicd.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> The reason it's giving you those errors is because NM isn't working right. If you can manage to get a LAN connection to the router you use, I would suggest doing that and trying to get wicd again. I know how you feel, as I got sick of dealing with NM :) If you get wicd through synaptic, it should download the necessary files for wicd, and then carry out with the removal of NM and then the install of wicd.

Thanks for the quick reply!  Although, I'm not too savvy on terminology, so I have a few questions about your advice.

What exactly is a LAN, in laymen terms?  Right now I'm connected to the wireless router through a cable (an ethernet cable?), so I do have an internet connection to this laptop.  I tried downloading Wicd through Synaptic by using the following instructions:

"Installing Wicd in Ubuntu If you are using Ubuntu Jaunty, Wicd is in the universe repository, so a simple sudo apt-get install wicd will do it. If you want the latest version of Wicd when it comes out, though, you'll need to add the Wicd repository. Jaunty users who need to download the Wicd deb package can grab it from [Ubuntu's Universe repository]("http://packages.ubuntu.com/jaunty/all/wicd/download").
  Non-Jaunty versions of Ubuntu (Intrepid, Hardy, etc) or Jaunty users who want the latest updates will have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line: 
[INDENT] deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras [/INDENT] where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid).   You'll also need to add the key used for signing Wicd by running the following command in a terminal: [INDENT] wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - [/INDENT]Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily."


However, when I hit Reload, it gave the following error message:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://apt.wicd.net/dists/hardy/Release](http://apt.wicd.net/dists/hardy/Release)  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead."

Is there another way to download it?

---

### Post by phantom3113 on 2009-05-06
A LAN connection is basically a cable (I probably should've put ethernet cable, but I forgot what it was called :P) It sounds like synaptic itself might be having trouble connecting, as I think it goes through your internet controller, and then starts downloading, but NM appears to "broken". Try going here [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download) and downloading the deb package from one of the mirrors (if that works, then something may be wrong with synaptic) If you can't get it to download still, that should mean that NM is officially broken. If that's the case, try getting the deb package from a different computer and transferring it to your ubuntu computer and then try installing it.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> A LAN connection is basically a cable (I probably should've put ethernet cable, but I forgot what it was called :P) It sounds like synaptic itself might be having trouble connecting, as I think it goes through your internet controller, and then starts downloading, but NM appears to "broken". Try going here [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download) and downloading the deb package from one of the mirrors (if that works, then something may be wrong with synaptic) If you can't get it to download still, that should mean that NM is officially broken. If that's the case, try getting the deb package from a different computer and transferring it to your ubuntu computer and then try installing it.

Okay, I'll give this a try, but does it matter that the link you gave me says "jaunty" and my Ubu is "hardy"?

---

### Post by phantom3113 on 2009-05-06
I'm honestly not sure if that would make a difference, but this page has a platform-dependent deb of wicd if you want to try that [http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059)

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> A LAN connection is basically a cable (I probably should've put ethernet cable, but I forgot what it was called :P) It sounds like synaptic itself might be having trouble connecting, as I think it goes through your internet controller, and then starts downloading, but NM appears to "broken". Try going here [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download) and downloading the deb package from one of the mirrors (if that works, then something may be wrong with synaptic) If you can't get it to download still, that should mean that NM is officially broken. If that's the case, try getting the deb package from a different computer and transferring it to your ubuntu computer and then try installing it.

I just tried downloading it and received this error message:

*Error: Conflicts with the installed package 'network-manager'*

Should I try removing Network Manager with the Add/Remove program and then try downloading this?  And if that doesn't work, how can I get it onto this laptop?  Could I download it to another computer, email it to myself, and then open up the email in this laptop?  Cos this laptop doesn't have a CD drive, so I can't burn the thing onto a CD.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> I'm honestly not sure if that would make a difference, but this page has a platform-dependent deb of wicd if you want to try that [http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059)

I just tried this link too, and it gave me the same error message.  Oh, and the error message appears in the Package Installer, which is what opens up when I try click on the wicd_1.5.9_all.deb file to open it.

---

### Post by phantom3113 on 2009-05-06
I was afraid it was going to do that. Try going into synaptic package manager and where it lists different categories on the left, go to Networking (just networking, not universe, nonfree, etc). Find the packages titled "network-manager" and "network-manager-gnome" and mark them for complete removal. A word of caution though, this will probably render you completely internet-less! If it removes network manager successfully, AND you still have internet connection through the cable, try wicd again. If you don't have internet, you could probably put wicd onto a flash drive (I assume your computer has a USB drive?)

---

### Post by phantom3113 on 2009-05-06
> **francopdx said:**
> I just tried this link too, and it gave me the same error message.  Oh, and the error message appears in the Package Installer, which is what opens up when I try click on the wicd_1.5.9_all.deb file to open it.

It gave you an error message? Make sure that if it gives you the option to open or save it, that you choose to save it (and then double-click it when done)

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> I was afraid it was going to do that. Try going into synaptic package manager and where it lists different categories on the left, go to Networking (just networking, not universe, nonfree, etc). Find the packages titled "network-manager" and "network-manager-gnome" and mark them for complete removal. A word of caution though, this will probably render you completely internet-less! If it removes network manager successfully, AND you still have internet connection through the cable, try wicd again. If you don't have internet, you could probably put wicd onto a flash drive (I assume your computer has a USB drive?)

Okay, I'll give this a shot through the synaptic package manager.  This laptop does have a USB slot, but I don't have a flashcard.  Although, it looks like the wicd file from those links you posted has been downloaded... it is just not loading because of the conflict with network manager, so hopefully once NM is gone, the wicd loads properly.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> It gave you an error message? Make sure that if it gives you the option to open or save it, that you choose to save it (and then double-click it when done)

I did save it.  Saved it from both the links you provided, and after I double-clicked the saved files, that is the error message that appeared in the Package Installer (which is what opened when I double-clicked on the files).

---

### Post by phantom3113 on 2009-05-06
I'm hoping. I've got my fingers crossed for you :)

*about the error messages: I thought you meant it gave you those when downloading it. Sorry :P*

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> I'm hoping. I've got my fingers crossed for you :)

*about the error messages: I thought you meant it gave you those when downloading it. Sorry :P*

I removed NM and installed Wicd on my laptop, but when I open Wicd, it gives me this message:

"No wireless networks found."

How do I connect to my wireless network?  If it matters, I used the file downloaded from the second link you gave me (but I also have the file from the first link on my laptop too... I downloaded them both).

---

### Post by phantom3113 on 2009-05-06
Ok, at this point it may just be a driver issue/wicd preferences. Could you post the output of "lspci" and "lsusb" from a terminal? (No quotes)

*If your network is hidden, you may have to manually add it

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> Ok, at this point it may just be a driver issue/wicd preferences. Could you post the output of "lspci" and "lsusb" from a terminal? (No quotes)

*If your network is hidden, you may have to manually add it

Getting closer... after a few minutes, the Wicd detected my wireless network (along with a couple other ones in the neighborhood) all by itself... I didn't even get around to doing your latest advice... so that's the good news.  The bad news is that I'm still having some difficulty connecting.  I think the problem now is our password...

When I click on the "Connect" button for our network, a message comes up saying, "This network requires encryption to be enabled."  I believe that means I need to enter my password, so I click on the "Advanced Settings" button.  In the "Advanced Settings" window, I check the "Use Encryption" box and type our password into the "Key" line.  The one problem is that I don't know what option to select from the drop down menu that lists things like WPA 1/2 (Passphrase) and WEP (Hex).  I think with Network Manager, the option selected had (ascii) in the parenthesis, but I don't see that option available here in Wicd.  Suggestions?

---

### Post by phantom3113 on 2009-05-06
Do you know what kind of encryption your network uses? The list of options wicd has can be pretty extensive and sometimes confusing.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> Do you know what kind of encryption your network uses? The list of options wicd has can be pretty extensive and sometimes confusing.

I have no idea about the type of encryption.  There are only about 10 options in the "Advanced Settings" drop down menu, and I've tried them all, but nothing seems to work.  Maybe some more info will help...

When I look at my network (Ballaz) in the Wicd Manager, it says:
Ballaz 100% WEP 00:22:3F:32:5D:E0

When I click on the little side arrow (>), it turns to face downward (opposite of "^") and reveals the following info:
Ballaz 100% WEP 00:22:3F:32:5D:E0 Managed Channel 4
...along with the "Scripts" and "Advanced Settings buttons" just below.

The encryption options are:
WPA 1/2 (Passphrase)
WPA 1/2 (Preshared Key)
WEP (Hex)
WEP (Passphrase)
WEP Shared/Restricted
LEAP with WEP
TTLS with WEP
EAP-FAST
PEAP with GTC
PEAP with TKIP
EAP-TLS

The first 5 options give only the "Key" text box, and that's where I enter the password.  The rest of the options give several text boxes that include things like Username and Identity and other fields which I never saw before (and therefore never had to fill in) with the way I did it in NM.


AfterI put in the password and close the "Advanced Settings" window, I click connect, and as it is "Connecting...", the following messages appear:

Putting Interface Down
Validating Authentication
Ballaz:  Obtaining IP Address...

The WPA options get stuck on "Validating Authentication" but the WEP options go to "Ballaz:  Obtaining IP Address..." and get stuck there.  In either attempt, it eventually just stops trying to connect.

---

### Post by phantom3113 on 2009-05-06
ok, your connection uses WEP encryption, so the type to specify will be one of the WEP options (obviously :P ) Is your password a 26 digit numeral/alphabetical code? If it is, select the WEP (HEX) option and put in the passcode (checking the tickbox next to the field will show your password so you don't mistype it) You shouldn't need to do anything with any other box under the advanced settings window. If your key is just a phrase or something like that, try WEP (PASSPHRASE) and then try connecting. On my computer, the wicd window goes black and looks like it freezes, but it's actually working on connecting (not sure if it does the same thing to you). I've found that when it says "Obtaining IP Address..." that normally means it's succeeded in connecting and is just finishing up.

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> ok, your connection uses WEP encryption, so the type to specify will be one of the WEP options (obviously :P ) Is your password a 26 digit numeral/alphabetical code? If it is, select the WEP (HEX) option and put in the passcode (checking the tickbox next to the field will show your password so you don't mistype it) You shouldn't need to do anything with any other box under the advanced settings window. If your key is just a phrase or something like that, try WEP (PASSPHRASE) and then try connecting. On my computer, the wicd window goes black and looks like it freezes, but it's actually working on connecting (not sure if it does the same thing to you). I've found that when it says "Obtaining IP Address..." that normally means it's succeeded in connecting and is just finishing up.

Our password is definitely not 26 digits long.  It is 10 digits long, and they happen to all be numbers, but I think that was just by chance (not a requirement for it to be all numbers).  When I try it with the 3 different WEP options, it always get to the "Obtaining IP Adress..." part but it never actually just connects.  Just stops connecting after about a minute or so.

---

### Post by phantom3113 on 2009-05-06
That's...odd. If you don't mind changing your password, try going into your router (put 192.168.1.1 into the address bar) and adjusting the encryption settings. I believe that a 128 bit WEP would be the 26 digit code. Just to clarify, in the connections screen for wicd, it does say WEP next to the name of your connection right? (see the screenshot)

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> That's...odd. If you don't mind changing your password, try going into your router (put 192.168.1.1 into the address bar) and adjusting the encryption settings. I believe that a 128 bit WEP would be the 26 digit code. Just to clarify, in the connections screen for wicd, it does say WEP next to the name of your connection right? (see the screenshot)

Correct about the WEP next to the connection name.

The password is used by a few people, so I'd have to see if changing it would mess up any of their systems.

And is there anything besides Wicd that I could try using?

---

### Post by phantom3113 on 2009-05-06
I've also heard of wifi-radar, although I've never used it so I have no experience with it. I found this in a search about wicd encryption:

> Just select WEP (HEX) and make sure you are using HEX, if you use asii, that is Windows and Ubuntu will not be able to authenticate.

That was from another thread on the ubuntuforums somewhere and I remember you said that NM had an option with ascii next to it. From this, I assume that wicd won't be able to handle it, so I guess that getting wifi-radar or else changing the encryption key is your only choice.

If you do change the passcode, the only thing you would have to do with the other computers that use it would be to adjust their settings so they have the right one.

*Just found this on the same page. It can change your password into a hex-code if you want to use the "same" passcode [http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

### Post by francopdx on 2009-05-06
> **phantom3113 said:**
> I've also heard of wifi-radar, although I've never used it so I have no experience with it. I found this in a search about wicd encryption:



That was from another thread on the ubuntuforums somewhere and I remember you said that NM had an option with ascii next to it. From this, I assume that wicd won't be able to handle it, so I guess that getting wifi-radar or else changing the encryption key is your only choice.

If you do change the passcode, the only thing you would have to do with the other computers that use it would be to adjust their settings so they have the right one.

*Just found this on the same page. It can change your password into a hex-code if you want to use the "same" passcode [http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Okay, I'll see if we can switch our password setting, and if not, I'll look into that other program.  Either way, I'll let you know how it goes, and THANKS for all the help!!!  It is most appreciated!!!  :P

---

### Post by phantom3113 on 2009-05-06
No problem at all, glad to have helped :)

---

### Post by francopdx on 2009-09-01
> **phantom3113 said:**
> No problem at all, glad to have helped :)

Twice now my attempt to reply has resulted in my entire post being deleted with posting!

Anyway, I have a new problem.  I tried using my printer (Lexmark Z611) with this laptop, but it doesn't seem to work.  I receive this error in the "Printer configuation - localhost" settings screen:

"There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Any ideas on how to look into fixing this?

---

### Post by dbalascak on 2009-09-01
sorry. mis-type

---


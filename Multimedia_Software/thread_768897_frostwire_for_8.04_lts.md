---
title: "frostwire for 8.04 lts"
date: 2008-04-26
forum: Multimedia Software
---

### Post by krysia on 2008-04-26
has anyone downloaded frostwire for the new ubuntu 8.04,I have tried but so far no luck,so if anyone has perhaps they could walk me through the process.
I had frostwire working with 7.10 and I upgraded to 8.04 by directly downloading it to my hardrive could this be the problem.
perhaps I was being lazy but I did'nt want to re-install everything again and there is no problem with any of the other programs ie.skype .
I don't want limewire because I had a bad experience with it while using windows.
looking forward to any help.
krysia.

---

### Post by HandyAndy on 2008-04-26
I downloaded it from here:

[http://www.frostwire.com/?id=downloads]("http://www.frostwire.com/?id=downloads")

Firefox's download manager offered to install it using GDebi and it worked fine, including adding a menu item.

My only trouble now is that Frostwire can't connect to the Gnutella network - it says the port it uses is blocked. Any ideas anyone?

---

### Post by cor2y on 2008-04-26
change the port or forward the port using firestarter if you need the gui method  and don't forget to forwrad the hardware firewall as well if you use a router.

---

### Post by HandyAndy on 2008-04-26
> **cor2y said:**
> change the port or forward the port using firestarter if you need the gui method  and don't forget to forwrad the hardware firewall as well if you use a router.

Thanks, cor2y, but I need a bit more hand holding.
How do I change the port?
How do I forward the port?
What/where is firestarter?
I have got a router with a firewall; how do I forward that?

---

### Post by cor2y on 2008-04-26
Edit
Found this at the frostwire forums.
> 
This should help if you are having problems getting your connection status up from starting connection. Feedback on whether it helps or not would be greatly appreciated. Please post in this thread. But first try this: go to Frostwire > file > disconnect and then back to file > connect. That sometimes does the trick. 

[COLOR=brown]Before that ensure you are running the latest version .. currently 4.13.5, which has rectified many connecting problems, from Home or Downloads above
[/COLOR] 
----------------------------------------------------------------------- 

Windows users can do this simply with a patch introduced 15 January 2008, The patch will work with XP and Vista. Please Try it and all feed back from all Windows users would be greatly appreciated. Our thanks to FTA for this patch. 

The instructions are simple: 
1. Download zip file from [http://www.mybloop.com/FTA/fixconnecting.zip](http://www.mybloop.com/FTA/fixconnecting.zip) 
2. Close FrostWire *completely* if it's running  
3. Open the zip file and then click on 'fixgnutella.exe' 

The exe file is virus free and it should be running without problems, but in very rare situations could need some kind of "DLL" or additional files. 

----------------------------------------------------------------------- 
For other platforms, and for Windows if the mybloop.com site is unavailable: 

In your application data or preference folder for Frostwire, (not your program or applications folder) there should be a file entitled gnutella.net and this file should be approximately 20-30kb in size. 

If the file is approximately 4 kb in size or does not exist at-all the following will explain how to replace it. Before making any changes to the Folder, make sure Frostwire is fully closed. You need do nothing else with the file .. just put it in the folder .. Frostwire knows what to do with it [IMG]http://www.frostwire.com/forum/images/smilies/icon_smile.gif[/IMG] 

**Download fresh gnutella.net file**. 
A fresh gnutella.net file (Created 22 Jan 2008 ) can be downloaded from the following link. PLEASE NOTE: You must Right Click (Ctrl Click on Mac) on the Link and select save as, or save link or target as. 
[www.clockworkgeek.com/gnutella.net]("http://www.clockworkgeek.com/gnutella.net") 
Download/Save this to your desktop, or somewhere you can find it. There are various sources for the file and some of them are dubious. This one is not. If you have a working copy of Limewire or Frostwire possibly on another computer you can copy the file from that application, to a memory stick, if necessary and use that instead. 


**Find your Preference or Application Data Folder**. Note: this is not your Application or Programme Folder. 

To find your preference folder in Mac OS X it is in HD>users>your name>library>preferences>Frostwire, and the gnutella.net file will be in that folder 

In Windows XP on your start menu click Run... and type in %appdata% A folder will appear, look for Frostwire and inside for gnutella.net 

In Windows Vista Open any folder window and type %appdata% in the box at the top. A folder, or list will appear, look for Frostwire and inside that, for gnutella.net 

alternatively: 

in Windows XP the folder is at C:\Documents and Settings\name you use to login\Application Data\FrostWire\ and look for gnutella.net 

in Windows Vista it is at C:\Users\name you use to login\AppData\Roaming\FrostWire\ and look for gnutella.net 


Your app data folder is quite likely hidden and you may need to enable it to be visible. in any windows folder click tools > folder options at the top. click on that and then view then show hidden files and folders. 

**Now make sure Frostwire is fully closed** 

Now check the size of your gnutella.net file. If it is around 4kb delete it and move the file you downloaded into the folder in its place. If no gnutella.net file exists move the new file into the folder. 
If the gnutella.net file is around 20kb you should not need to change it ..... but if you do and it makes a difference please let us know and also paste the first 20 lines or so of your old gnutella.net file here which might be useful .. you can post it all if you like [IMG]http://www.frostwire.com/forum/images/smilies/icon_smile.gif[/IMG] 

Restart Frostwire and see if it reaches turbocharged connection within a few minutes or less. 

[COLOR=brown]no português:[/COLOR] [http://www.frostwire.com/forum/viewtopi ... php?t=3548]("http://www.frostwire.com/forum/viewtopic.php?t=3548viewtopic.php?t=3548") [COLOR=brown]obrigado a _Teen_[/COLOR]

---


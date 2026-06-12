---
title: "Ralink wireless g pcmcia wifi card"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by wlamore on 2010-03-11
[COLOR=black][FONT=Verdana]I just purchased a RALINK WIRELESS G PCMCIA WIFI CARD VISTA/LINUX (UBUNTU)[/FONT][/COLOR][COLOR=black][FONT=Arial]&#8207;[/FONT][/COLOR][COLOR=black][FONT=Verdana].[/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]It is supposed to be UBUNTU plug and play out of the box with no driver downloads needed. [/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]I installed it but could not find a way to search the active Wi-Fi networks available like on my Actiontec card on windows xp. The wireless router/ethernet I have is an Actiontec setup for Qwest-DSL and Actiontec is the name of the wireless network. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Strangely I tried to choose setup a "new network" and entered Actiontec as the network name and it found the network and said it was connected to it. However the internet still is not working?? [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Any ideas would be appreciated. I am trying to make the switch from windows to Linux but it is a "learning experience" any good guides to getting proficient in Ubuntu would be a + if someone can suggest one that is for beginners![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]wlamore[/FONT][/COLOR]

---

### Post by Naggobot on 2010-03-11
First if you have not yet done so, connect your computer to wire and update (system -> administration -> update manager) I installed ubuntu last week and did it twice since I did not run the update after the installation. I did the second installation with wired network and everything worked. It would have been enough just to update the first install. Stupid of me. 

Second, if you are using WEP check that you have correct setting on key shearing i.e open network or shared key. I do not know about Ubuntu but Windows can (or at least could) connect to shared network with open key and behaviour was as you described. 

Thirdly
I am a newbie my self so I can not offer 100% certain answers. I can tell what hardware I have and what I did to set it up. 

My first recommendation is that you wait a while an see if someone confirms anything I say before trying what I write below. 

I use (or actually my computers since I do not yet have wireless integrated:D ) broadcom STA driver. In order to get it working I selected 

system (from the top menu) -> administration -> hardware drivers 

then I selected search for available drivers after the system searches for hardware and detects the correct wifi device. 

You can try this first to see if there is proprietary driver available. 

Second thing you can safely (in my opinion) try is select

system-> administration -> synaptic pakage manager 

on top menu there is a search box, write "ralink" and you will find ralink related pakages. 

I have 5 listed, one of them is rt73-common others are source files. I would not tamper with those since there is nothing I could do with them. 

Check rt73 if (note if) your device is rt73 i.e. fits the description. 

Install and see what happens. If it does not work then uninstall the drivers. 

Note: for both cases you need wired network.

Fourthly I suggest that you post accurate info on your wifi hardware (i.e. is it forementioned RT73 (RT2571W) or something else. Then those that have more info are better able to help you.

edit:

I was browsing through forums and found this
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network)
Check it out if you can find a solution for your problem there

---


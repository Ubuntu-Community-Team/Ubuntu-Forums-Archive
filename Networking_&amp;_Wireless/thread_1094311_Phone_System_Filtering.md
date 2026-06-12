---
title: "Phone System Filtering"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by Keymaster on 2009-03-12
Edit: How can I configure Asterisk on a PC to use my Optimum Voice (from Cablevision) to filter incoming calls via a blacklist?  I only have the PCI modem card that came with the tower.  Running Ubuntu 8.04.1 Server

---

### Post by Elludium_Q-36 on 2009-04-30
For the basic system, more info is needed unless someone else who's been in the exact same boat steps up...
You're putting the cart before the horse.

I looked at [http://www.optimum.com/voice/index.jsp](http://www.optimum.com/voice/index.jsp)  ...
So you have cable internet data and voice...
I'm assuming they put an ATA someplace or the data modem has an ATA port...  So it would seem that your calls are already routed with a SIP...  Why make a convoluted system unless you intend to go back to POTS?  Instead of the ATA, use the H.323/SIP/VoIP primarily to bring the calls directly to the Asterisk server.  Go with Kiax/Iax or other H.323/SIP/Voip client software with headphones/mic and maybe WiFi handsets.  If you are stuck on POTS, send the wanted calls via the ATA.  Otherwise the modem needs to be a voice modem:

[http://ubuntuforums.org/showthread.php?p=7181848#post7181848](http://ubuntuforums.org/showthread.php?p=7181848#post7181848)

Asterisk has caller I.D. support and advanced call routing.  You could route certain calls to a busy signal...
Grandcentral.com blocks calls from selected numbers but subscribers will be compelled to convert to google voice...

I could see sticking with analog phone technology as a backup, IF YOU WERE SERVICED BY THE TELCO'S POTS but that's not the case.

Power failure is one arguement for the POTS backup.
I'd recommend a UPS/surge protector.

You could also put asterisk on a low power device, such as a router...
[http://www.voip-info.org/wiki/view/Asterisk+Linksys+WRT54G](http://www.voip-info.org/wiki/view/Asterisk+Linksys+WRT54G)

---

### Post by Keymaster on 2009-04-30
My router is an ubuntu server so I can't use a WRT54g.  Also I'm not familair with the terms ATA or POTS when in regards to phones. (POTS I don't know at all)  The setup CV gave us was a cable modem with a phone wire from the wall coming into it, and then the rest of the phones in the other walls just work (like an ethernet switch for phone wires)  Not sure how to go about adding asterisk for call filtering (by number)  I do want to send the filtered (blocked 800 numbers, annoying relatives) to either a never ending ringing that we dont here, or more preferably some type of audio file that will play a "you have been blocked" message, and then hang up on them)

---

### Post by Elludium_Q-36 on 2009-05-06
I understood what you want from your Original Post but apparently you are not reading me.
[Are your boots laced]("http://www.urbandictionary.com/define.php?term=are%20your%20boots%20laced")?
I don't see anyone else attempting to steer you in the right direction...
 
First you have to address the hardware issue.
You did not post what modem hardware CV gave you but it assumably functions as an ATA and the installation "Tech" probably just snipped the "ring" & "Tip",  commonly red and green insulated bell wire at the customer interface (or maybe unplugged the modular jack).  Usually the telco does an office disconnect but it might not like power and ring being back fed plus some telcos leave 911 only service or what cell customers know as restricted 611 service.  Also sending voltage to the telco's equipment would draw down your ATA.  Neither here nor there but you probably have an ATA/FXS jack on your cable modem.
 
"Ethernet switch for phone wires"?????  [Are you slaggin' the Lagan]("http://www.urbandictionary.com/define.php?term=Are%20you%20slaggin%27%20the%20lagan%20%3F")?
 
[Let me introduce you to a web concept]("http://lmgtfy.com/?q=define%3Aata").
Via that link, I see another linked definition including the word telephone. f you click that other link, you will also see a definition for POTS
 [Are your boots laced]("http://www.urbandictionary.com/define.php?term=are%20your%20boots%20laced")?  

Let's not forget [FXS]("http://lmgtfy.com/?q=define%3Afxs").
 
From what you described you have a cable modem which makes a digital Ethernet connection but you want it's Analog ATA to feed through an unknown and probably unsupported [pstn]("http://lmgtfy.com/?q=define%3Apstn") modem to asterisk then have another ata pci card run your dinosaur analog phones?  [Are you slaggin' the Lagan]("http://www.urbandictionary.com/define.php?term=Are%20you%20slaggin%27%20the%20lagan%20%3F")?

 
I have read that there are two varieties of "know it all";  the ones who know their stuff and those who are full of stuff you'd find in a cow pasture...  You can find plenty of the latter on the forums and even in [CSR]("http://lmgtfy.com/?q=define%3Acsr") or "tech support" positions.  Often the tech support "help desk" is helpless and they just read from scripts.  I try to know my stuff.
 
I will try to explain differently.  It seems that you are contemplating something convoluted.  
You see: **"[Asterisk needs no additional hardware for Voice-over-IP]("http://www.voip-info.org/wiki/view/Asterisk")"** 
You already have data AND phone digitized!  You may not realize that you have a [Rube Goldberg machine]("http://en.wikipedia.org/wiki/Rube_Goldberg_machine") in the making...  You're coming in digital, out analog, back through your Ubuntu box's voice modem (which may not be supported) which hands the data-stream digitized to Asterisk... Now what, you get ANOTHER FXS/ATA card to send it back out to your analog phones?  If you're stuck in THAT loop, better to get a Digium card or knock off, which has up to 4 [fxo]("http://lmgtfy.com/?q=define%3Afxo") & 4 [fxs]("http://lmgtfy.com/?q=define%3Afxs") jacks native...

 
Now the thing about generic voice modems in the short answer is that they may not work well with Asterisk.
Some cheaper generic cards need [smt]("http://lmgtfy.com/?q=define%3Asmt") [desodering]("http://www.google.com/search?btnG=1&q=define%3Adesoldering") modification to work marginally.  Echo cancellation is one issue and it is preferred to use a hardware card add-on module since software cancellation puts a major draw on cpu resources.   Asterisk itself draws much CPU load and that's why it is recommeded to have dedicated hardware (a [dd-wrt]("http://lmgtfy.com/?q=define%3Add-wrt") set-up or pricey [digium]("http://www.digium.com/en/") standalone, for example)
 
I don't know what you mean that your "router is an Ubuntu server".  You have a DEDICATED Ubuntu server tower with the PCI modem that you don't use as a desktop workstation but it's a router because you have mutiple nic/Ethernet cards (pretty old school, pre modern router)?  You run a server on a [NAS]("http://en.m.wikipedia.org/wiki/Network-attached_storage") router.  It's a modern router or a tower?  Whatever configuration, if it's a router/gateway, it talks DHCP/NAT in ipv4 and should be ipv6 compliant and there's no reason that other routers can't be put downstream.   
 
The wrt54g was an example but [it does not make sense that a farmer can utilize one and you could not]("http://www.voip-info.org/wiki/view/Asterisk+Linksys+WRT54G").
Perhaps it's correctly said that you would not than could not. 
*    [I would not, could not, in a box]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I could not, would not, with a fox]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I will not eat them with a mouse]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I will not eat them in a house]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I will not eat them here or there]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I will not eat them anywhere]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I do not eat green eggs and ham]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon").
*    [I do not like them, Sam-I-am]("http://en.wikipedia.org/wiki/Green_Eggs_and_Ham#Lexicon"). 
I would, could, have and will, with a fox and in a box...
And I'm not only talking about firefox in a linux box...

Also, you also totally missed the point for the recommendation of a low power consumption device like a WRT54G!
I wrote:
"Power failure is one argument for the POTS backup. I'd recommend a UPS/surge protector.  You could also put asterisk on a low power device, such as a router...  http://www.voip-info.org/wiki/view/A...Linksys+WRT54G"
Of course this advice is only good for someone who listens and learns to ask the right questions...
Most people wonder why their cordless phone doesn't work when the power company isn't sending power.
I guess trying to explain that the cable modem, router, asterisk server and [line power]("http://lmgtfy.com/?q=define%3Aline+power")ed telephone devices need to be plugged into a UPS or battery would be a waste of time!  But perhaps someone else will benefit from this.

 
Digium successfully sells dedicated hardware because of the cpu load and those can go for grand or two, plus the annual support...  their cards with FXS / FXO ports are not so bad but you'd need to limit the other expectations on the system and most people use a dedicated server.  Seems like you have a residential/[SOHO]("http://en.wikipedia.org/wiki/Small_office/home_office") application...
So you only need SOHO connectivity and not an [enterprise router]("http://en.wikipedia.org/wiki/Router#Small_Office_Home_Office_.28SOHO.29_connectivity").
 
I'm assuming it was not your intention to peave me off but you replied with a No (regarding the WRT54g).
People do not like giving free advice and having the big no thrown back; whether or not it's [non sequitur]("http://lmgtfy.com/?q=define%3Anon+sequitur").
If I see someone pull out a blackberry 7520 and I small-talk-ing-ly say, "Oh well at least you've got a blackberry." and their comeback is "No, it's a Nextel!";  I might be inclined to bludgeon them.
When I taught "behind the wheel" driver's education, the kids loved me and hated the classroom instructor.  He asked what the first thing the students should do after getting in the car and one answered, "Buckle up."    "NO!  You fasten your seatbelt!"   Images of Pink Floyd's "The wall" music video come to mind.  "WRO-UNG!  Do it again."  "If you don't eat your meat, you can't have any pudding.  How can you have any pudding if you don't eat your meat?"  Since that song was released circa 1979, I'd venture a guess that [mad cow disease for englanders]("http://en.wikipedia.org/wiki/Bovine_spongiform_encephalopathy#The_BSE_epidemic_in_British_cattle") must have predated official 1986 scare and they should have instead had more Irish potatos...
Winning friends and influencing people does not begin by contradicting people, whether they are right or wrong!
 
[Are you slaggin' the Lagan]("http://www.urbandictionary.com/define.php?term=Are%20you%20slaggin%27%20the%20lagan%20%3F")?
 
It seems that you are not familiar with IAX (Inter Asterisk eXchange).  Multiple asterisk servers often work together.  Why would a WRT54g used for Asterisk not be able to communicate with another asterisk server or client?  I have Kiax and iaxcomm clients on my machine and with that I can access POTS lines (Plain Old Telephone Service) on Asterisk servers anywhere on the planet!  From home, I can work for any business in the world and accept calls via their teleco interconnect and place calls from their lines while the clients and customers think I'm sitting in the same office as the asterisk server that's directly connected to the PSTN (Public Switched Telephone Network).  There's also an Asterisk ability to patch into two way radios so I could dispatch radio communications from anywhere.  One should also be able to connect to iDEN or 3G/4G PTT (Push To Talk) handsets like in Motorola's "[Dispatch Manager]("http://www.fleetcom.ca/features/index.asp?subNav=5")".  
 
Now I assume that since you are a linux user, you don't swallow [all the trite that gets packaged through the pipeline]("http://catb.org/~esr/jargon/html/S/SNAFU-principle.html").  Unless Asterisk is the only reason for your interest in linux/Ubuntu...
 
I glanced at some of your other posts...  Seems like you are more software oriented...  Software/firmware and hardware must be intergrated into a fluid, scalable system.  To do that you must have a good understanding of all factors involved and [not receive dictation from those who do not]("http://www.nhatban.net:2010/?db=foldoc&pos=1198")...
There are offices where people type things on a computer, print it out, then feed it into a fax machine.
At the other end, someone takes the fax and types it into a computer...
Both places have data/fax modems in their desktops AND e-mail.
Is this what you wish to do?
 
With your setup, a less complicated AND LESS EXPENSIVE method would be to let the modem/ATA to route the sip/H.323 data-stream over Ethernet through the router as digital/VoIP to the asterisk server.  **AS I WROTE IN MY FIRST POST IN THIS THREAD**,  It might be cheaper to get Voip/WiFi phones.  Otherwise and according to your intent to stick by your analog, you'd need an FXS card.  CV should not care if you use their service in analog or digital mode.
 
Why do you even need their cable modem with an ATA if you have asterisk?  It's cheaper to buy a used modem than to pay a rental fee.
 
If you're really stuck in the analog loop, buy an unlocked ATA router and tag that to the asterisk server but it may be possible to route the data-stream back to the CV modem/ATA after it has been handled by asterisk...
 
See if CV runs an asterisk service if you are stuck on the idea of [what you need is what they're selling]("http://lyricwiki.org/Rage_Against_The_Machine:No_Shelter").
 
I already mentioned [http://grandcentral.com](http://grandcentral.com) , soon to be Google voice; which blocks calls.
Maybe Vonage blocks calls...
 
Many Asterisk setups, SOHO or big ones, have NO analog and therefore NO PSTN modem so why do you need to do so?
 
If you don't want to take my advice, call Bill Gates and [do what he told ya']("http://lyricwiki.org/Rage_Against_The_Machine:Killing_In_The_Name").
 
By the way, "KeyMaster";  You will find H.323 GateKeepers in the Ubuntu packages....
"I am the keymaster.  Are you the gatekeeper"
 
"There's no place like 127.0.0.1"

---

### Post by Keymaster on 2009-05-07
I appreciate the very large reply, and the detailed explanation.  I have decided to contact CV about blocking numbers for us, and I will await their response.  In the mean time this project is on hold, and I will record your info for later use.  Thanks again.

---

### Post by Elludium_Q-36 on 2009-05-14
The information that you seem to want can be found via this link:
[URL="http://www.privacyrights.org/fs/fs3-hrs2.htm"]
http://www.privacyrights.org/fs/fs3-hrs2.htm[/URL]

Read and re-read carefully and you will find several helpful links AND phone numbers.  
Linked products should be cheaper, especially in the long run, when compared to that which could be provided with your bundled telephone service.

I had a telezapper / inbound call blocker years ago and that worked well but I no longer need one with how I have evolved my overall telecommunications program 
(info on inbound call blockers can be found via the above link!).

Find the brand names/model names & numbers of the inbound call blockers you might like and search [ebay.com]("http://ebay.com") or [longisland.craigslist.org/sss]("http://longisland.craigslist.org/sss")  
and that should keep your project budget low until you evolve beyond the need for analog telephony.

Good luck.

---

### Post by Elludium_Q-36 on 2010-03-10
Many people scoff free advice.  Some company coming in to do an install wouldn't care, so long as your check clears.  Of course the system has to work reasonably well.

If I came into your SOHO (Small Office, Home "Office"), I would try to get you off the idea of Analog, unless it was for Failover/Failback (You can Google those terms).  You have no POTS/PSTN analog service, other than from the FXO port of your ATA.  However, it is sometimes easier to sell something to end users to accommodate what they already have...

You could use devices such as a Sipura/Linksys spa3000 pstn interface  [http://wiki.linuxmce.org/index.php/Sipura/Linksys_spa3000_pstn_interface](http://wiki.linuxmce.org/index.php/Sipura/Linksys_spa3000_pstn_interface)
This is set up for "hop on, hop off", which would make sense if service were delivered by a conventional teleco.
[IMG]http://wiki.linuxmce.org/images/a/a3/Spa3000_setup.png[/IMG]

I would have a look at asteriskNOW (asterisk.org/asterisknow | youtube.com/watch?v=ONOxNJquatk ) or LinuxMCE (linuxmce.com | [http://www.youtube.com/watch?v=gNaWUM4bX3I](http://www.youtube.com/watch?v=gNaWUM4bX3I) | [http://www.youtube.com/watch?v=ztUCnBx9fYU](http://www.youtube.com/watch?v=ztUCnBx9fYU) ), for easier self configuration.  An intermediate step is to use the services of a local systems integrator/installer.  Pluto (plutohome.com) has integrated LinuxMCE and sells items which seem to be set to "automagically" plug & play.

From the LinuxMCE Wiki, it installs over Kubuntu which is Ubuntu with the KDE GUI/graphical front-end (google Kubuntu / KDE).  However, the packages are NOT currently available in the Ubuntu repositories.

I'm considering setting up as a systems integrator and may go with Pluto for their product/tech support so they bear the product liability.  I MAY do this on Long Island but this remains to be seen...

HERE IS SOMETHING TO CONSIDER FOR YOUR APPLICATION:
Your main consideration for implementing Asterisk is to avoid nuisance/unwanted calls.
Keeping Analog in the loop BEFORE Asterisk, limits you to ONE line.  Going the VOIP route often opens up more options.  You can often place and receive more than one call on the same "line"  The old school phones could handle one circuit on the dial-plan (An asterisk term) while "soft phones" can handle others (google soft phone, soft-phone, softphone).  Doing things "your" way, your wanted calls will get a busy signal while the ones you don't want are ringing to nowhere.  Seems like a waste of the potential since your cable provider already delivers the call codecs digitally.

---


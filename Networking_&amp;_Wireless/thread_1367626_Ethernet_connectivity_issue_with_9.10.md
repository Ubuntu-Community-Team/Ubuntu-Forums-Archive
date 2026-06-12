---
title: "Ethernet connectivity issue with 9.10"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Woijee on 2009-12-29
[COLOR=Black][COLOR=#1f497d]The 9.10 install worked perfectly with no tweaks or adjustments to the default networking configuration that allowed both Ethernet and a wireless connection to be used on an older system (Pentium II processor, Asus motherboard) on a Comcast cable internet connection using a Linksys router.[/COLOR][COLOR=#1f497d]
[/COLOR][/COLOR]
  [COLOR=Black][COLOR=#1f497d]The same system was then connected to a Qwest DSL modem and worked flawlessly for two weeks. No problems using Firefox. Then the system stopped connecting to the Internet. Two teenage girls using the system said they did not make any modifications, which I confirmed was true.[/COLOR][/COLOR][COLOR=Navy] No networking changes although they could not tell me if they downloaded and installed any Ubuntu updates.[/COLOR]

  [COLOR=Black][COLOR=#1f497d]I[/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d] connected[/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d] two other systems (Windows XP and a Xandros/Debian Linux OEM build) to the Qwest DSL modem and they worked flawlessly. I added a L[COLOR=Navy]inksys router between the Qwest DSL modem and both previously mentioned  computers worked perfectly . The 9.10 Ubuntu machine, however, and was unable to get an HTTP connection.
[/COLOR][/COLOR][/COLOR]
[COLOR=Navy]I took the 9.10 system back to my house with a Comcast cable and Linksys router and it worked flawlessly. I downloaded and installed the latest updates thinking that might help when I brought it back to my friend's house with the Qwest DSL router.[COLOR=#1f497d] I hooked up the system to the Qwest DSL router, and, again, [/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d][COLOR=Navy]as unable to get an HTTP connection.[/COLOR][/COLOR][/COLOR]

  [COLOR=Navy][COLOR=#1f497d]I saw that while the  9.10 Ubuntu system showed network connectivity, and allowed me to download updates but not use HTTP via a browser. So, I checked the proxy and networking configurations and saw connectivity and was able to download Ubuntu updates but not use HTTP via a browser.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I installed another networking card and got that to work &#8211; in the sense it allowed me to also allowed me to download updates but not use HTTP via a browser. I plugged the cable into the original on-board Ethernet connection and got the same results.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I tried several different proxy configs to no avail, triple checked the Ethernet connection type, router settings, et al, and still could not get HTTP to work.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I went back to my original hypotheses that if the cables were good, and network card was good, and the system was working previously, then a new version or updates that were installed killed the HTTP in Firefox.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I revved back the Ubuntu install from 9.10 version to the more stable 8.04 version that most companies,  FreeGreek and others use. [/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I tripled checked the network connections to see if they were configured the same as the 9.10 install, and they were exactly the same.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]My conclusion is I think even though my system (Xandros /Debian OEM build) worked at at the Qwest DSL house, and the 9.10 build worked at my house with the [/COLOR][/COLOR][COLOR=Navy]Comcast cable and Linksys router[/COLOR][COLOR=Navy][COLOR=#1f497d], some kind of update hosed the HTTP connection and would not allow the browser on the 9.1 build to connect on[/COLOR][/COLOR] [COLOR=Navy][COLOR=#1f497d] Qwest DSL with or without Linksys router.[/COLOR][/COLOR]

[COLOR=Navy]If someone has an answer that has had a similar issue with 9.10 install, please post a reply.

thanks.
[/COLOR]

---

### Post by focwiz on 2009-12-29
> **Woijee said:**
> [COLOR=Black][COLOR=#1f497d]The 9.10 install worked perfectly with no tweaks or adjustments to the default networking configuration that allowed both Ethernet and a wireless connection to be used on an older system (Pentium II processor, Asus motherboard) on a Comcast cable internet connection using a Linksys router.[/COLOR][COLOR=#1f497d]
[/COLOR][/COLOR]
  [COLOR=Black][COLOR=#1f497d]The same system was then connected to a Qwest DSL modem and worked flawlessly for two weeks. No problems using Firefox. Then the system stopped connecting to the Internet. Two teenage girls using the system said they did not make any modifications, which I confirmed was true.[/COLOR][/COLOR][COLOR=Navy] No networking changes although they could not tell me if they downloaded and installed any Ubuntu updates.[/COLOR]


  [COLOR=Black][COLOR=#1f497d]I[/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d] connected[/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d] two other systems (Windows XP and a Xandros/Debian Linux OEM build) to the Qwest DSL modem and they worked flawlessly. I added a L[COLOR=Navy]inksys router between the Qwest DSL modem and both previously mentioned  computers worked perfectly . The 9.10 Ubuntu machine, however, and was unable to get an HTTP connection.
[/COLOR][/COLOR][/COLOR]
[COLOR=Navy]I took the 9.10 system back to my house with a Comcast cable and Linksys router and it worked flawlessly. I downloaded and installed the latest updates thinking that might help when I brought it back to my friend's house with the Qwest DSL router.[COLOR=#1f497d] I hooked up the system to the Qwest DSL router, and, again, [/COLOR][/COLOR][COLOR=Black][COLOR=#1f497d][COLOR=Navy]as unable to get an HTTP connection.[/COLOR][/COLOR][/COLOR]

  [COLOR=Navy][COLOR=#1f497d]I saw that while the  9.10 Ubuntu system showed network connectivity, and allowed me to download updates but not use HTTP via a browser. So, I checked the proxy and networking configurations and saw connectivity and was able to download Ubuntu updates but not use HTTP via a browser.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I installed another networking card and got that to work &#8211; in the sense it allowed me to also allowed me to download updates but not use HTTP via a browser. I plugged the cable into the original on-board Ethernet connection and got the same results.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I tried several different proxy configs to no avail, triple checked the Ethernet connection type, router settings, et al, and still could not get HTTP to work.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I went back to my original hypotheses that if the cables were good, and network card was good, and the system was working previously, then a new version or updates that were installed killed the HTTP in Firefox.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I revved back the Ubuntu install from 9.10 version to the more stable 8.04 version that most companies and FreeGreek and others use. [/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]I tripled checked the network connections to see if they were configured the same as the 9.10 install, and they were exactly the same.[/COLOR][/COLOR]
  
  [COLOR=Navy][COLOR=#1f497d]My conclusion is So, I think even though my system (Xandros /Debian OEM build) worked at your house, and the girls&#8217; system worked at my house, some kind of update hosed the HTTP connection and would not allow the browser to connect.[/COLOR][/COLOR]
[COLOR=Navy]
[/COLOR]
[COLOR=Navy]Or if someone has an answer as to how to get the 9.10 install to work, please post a reply.[/COLOR]

I had some apparent issues with Qwest DNS servers...see the following post...
[http://ubuntuforums.org/showthread.php?t=1361797]("http://ubuntuforums.org/showthread.php?t=1361797")

---


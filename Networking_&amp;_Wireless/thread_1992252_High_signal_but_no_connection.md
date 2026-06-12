---
title: "High signal but no connection"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by maniiacl on 2012-05-31
Hello,
My netbook Acer aspire one is getting wifi signal and two weeks ago connection was working great, after I installed 12.04 ubuntu I couldnt connect anymore although im still getting signal,
I thought problem would be fixed by installing again ubuntu 11.04 but still it doesnt work either,,,
What should I do now?
Thanks
My adater is Atheros communications. AR242x/AR542x Wireless

---

### Post by MichaelGld on 2012-05-31
Is there security on the wifi network? Were you prompted for a password? If you have security and were not prompted, tell your wireless device to "forget" that network, then scan and try connecting again. Had that happen to me with a new wireless extender getting a strong sinal but only the message, "unable to connect to 'SSID'".

---

### Post by maniiacl on 2012-05-31
> **MichaelGld said:**
> Is there security on the wifi network? Were you prompted for a password?.

Yes security password is showing , It keeps asking for password all the time eventhough Im sure put the correct password. 
I also tried with ethernet cable but nothing....It detect both cable and wireless but it wont connect
Thanks

---

### Post by MichaelGld on 2012-05-31
Maybe there's a character in your password that is somehow causing a problem. Try changing your password to something with no special characters (a-z, 0-9) and see if you can then connect.  If you are using a router, try rebooting it.

---

### Post by steeldriver on 2012-05-31
there are some problems with some of the Atheros cards and ath5k /ath9k drivers I think

there's a really good step-by-step debugging thread linked in the stickies at the top of the forum that tells you all the commands to run (lshw, lspci, lsmod etc)

also search here for the ath5k nohwcrypt option, that might be your issue but proper troubleshooting is required to tell for sure

---

### Post by maniiacl on 2012-06-01
> **steeldriver said:**
> there are some problems with some of the Atheros cards and ath5k /ath9k drivers I think

there's a really good step-by-step debugging thread linked in the stickies at the top of the forum that tells you all the commands to run (lshw, lspci, lsmod etc)

also search here for the ath5k nohwcrypt option, that might be your issue but proper troubleshooting is required to tell for sure

Thanks guys,but I could connect 2 weeks ago with no problems,and I think the problem is that I think I have two different controllers I saw yesterday, I have one atheros and realtek,Maybe this is the problem?
How can I enable only one controller?

---

### Post by steeldriver on 2012-06-01
really you should follow the troubleshooting procedure linked in the sticky threads at the top of the forum - if you don't we're just guessing and you may get bad advice:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

if you *really* want to disable (technically 'unmanage') a particular card under network-manager, you can do it in the NetworkManager.conf file

---


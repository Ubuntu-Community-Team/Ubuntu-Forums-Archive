---
title: "WPA from the command line"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by Zakhafr on 2009-10-02
Hi Ubunteros,

I'm trying to set up a Wifi connection "manually", eg:
- from Command Line/Editing files
- not using graphical software such as NetworkManager/WCID, etc...

I had no problem with Open connections or WEP protected connections.

If some wifi/Linux specialist comes around here, I'll like a little help/confirmation/corrections to what I found so far.

So my findings, when you do:

```
sudo iwconfig wlan0 mode managed essid MySSID key F1A015DDC9
```

**Assertion 1**: here the **key** is always a **WEP **key.
You have **NO** mean through this command to specify a WPA key.
From the key you specify, the system would try to guess if it is a:
- 40bits WEP key expressed as Hexadecimal (example above)
- 40bits WEP key expressed as ASCII
- 104bits WEP key expressed as Hexadecimal
- 104Bits WEP key expressed as ASCII

You can help the "guessing" process and specify an ASCII key prefixing the key with **s:**

**Assertion 2**: WPA keys are always presented as "passphrase" and therefore should always be entered as characters. It is much less confusing to users than WEP key than can have two different representation for the same key: ASCII and Hex.
Nevertheless, Hexadecimal WPA key **DO** exist. Some internet providers (in France) deliver modems with a preprogrammed hexadecimal key both for WEP and WPA.
In order to be able to use this key in WPA, you must "convert" it to passphrase. You can do so using the below command:

```
wpa_passphrase MySSID F1A015DDC9
```

This command will output the passphrase equivalent to the key you specify a the second parameter of the above command.


**To be done 3**: now you have the passphrase and can use it successfully with graphical tools.

I'm at this point of the process, and I'm exploring how I can now program my Wifi link without any graphical tools using this key.



_So the questions are:_
- are assertion 1 & 2 true. If not please feel free to make any relevant correction to my findings.
- do you have any pointers (links,...) to how I can set up my WPA connection "manually", now that I have successfuly guessed the passphrase!



*Keep up the good job!*

---

### Post by kevdog on 2009-10-02
See the link in my signature about manual network configuration.  You need to use wpa_supplicant for the authentication process.

---

### Post by Zakhafr on 2009-10-11
Many thanks Kevdog, it works!

So, as for my questions, I'm assuming

-1) is **true** (eg. iwconfig ... key xxxx / is **ONLY** Wep)

-2) is also **true**... and missing from your tutorial, as I have the passphrase, and have to convert it to "key" before insertion in the wpa_supplicant.conf.

-3) Thanks again for the pointer, it works fine.


*[Edit: thread marked as **solved**]*

---

### Post by kevdog on 2009-10-11
In response:

#2 - You can convert it to a hex passphrase or keep it as an ASCII passphrase.  Whatever you prefer
Please note the passphrase is supposed to be used in quotes whereas the hex key is not:

I borrowed this from wieman, but this is the process to generate a hex key:

wpa_passphrase <your_essid> <your_ascii_key>

Resulting in an output like...
Quote:
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}

---


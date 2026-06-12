---
title: "brcmsmac driver, not connecting to channel 12"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by scisteffan on 2012-04-03
My ubuntu 11 installation, complete with brcmsmac driver, with "iw reg set GB" and "iw reg set EU" (both times I have unloaded and reloaded the brcmsmac module and restarted network manager), is not connecting to wireless networks on channel 12 and 13, despite:
```

iwlist chan
wlan0     23 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)
```I've attached the kernel log that displays the connection errors. Is there a problem with the driver, a setting in ubuntu that needs changing, or any solution?

---

### Post by Martyn Thompson on 2012-06-03
I can confirm that this is still happening... 

Have looked at Launchpad and it is a confirmed bug.  Apparently something to do with ROW (rest of world) setting only defaults to channels 1 thro' 11.  

I have managed to 'open' my broadcom up to show that it *should* be able to connect to Channels 12 & 13 but it still fails.  Placing the wireless router back to channel 11 and it connects immediately (on prompting for password). 

Here is output from iwlist command: 

```
$ iwlist wlan0 channel
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.462 GHz (Channel 11)
```

Anyone got any ideas?  Thanks.

---


---
title: "Can't connect to https sites behind automatic proxy"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by SunShadow on 2012-11-15
Hello,
I'm using Ubuntu 12.04 32bit and I'm using Chromium v23.0.1271.64. Since I need to use a couple of different proxies depending on my location, I tried to set up a local .pac file and set Ubuntu proxy settings to "automatic".

The setup partially works, but I can't connect to https websites. I can connect if I set proxy settings to "manual", using the same ip address and port for every protocol; I also tried using the "Proxy SwitchySharp" extension for Chromium, and that works as well.

I've tried installing Firefox to see if the problem persists... and in Firefox I can't connect to https sites neither with automatic nor manual settings. I haven't looked in Firefox's settings very much though.

Here is a copy of my .pac file:

```
function FindProxyForURL(url, host) {   
  // First location
  if (isInNet(myIpAddress(), "10.10.109.0", "255.255.255.0"))
  {        
    return "PROXY 10.10.109.1:3128; DIRECT";
  }
  // Second location
  else if (isInNet(myIpAddress(), "10.10.105.0", "255.255.255.0"))
  {        
    return "PROXY 10.10.105.1:3128; DIRECT";
  }
  else
  {
    return "DIRECT";
  }
}
```

I'm currently connected from the second location.

Is there anything wrong with the file? Do I need to specify something to make it work with https?

Thanks in advance!

---


---
title: "problem with b43 (broadcom bcm4312) on lucid"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by Entheogen on 2010-07-20
hi,
i just installed ubuntu lucid on my new laptop (hp pavillion dv6) and I am having troubles with wireless. I installed b43 drivers and at first I could connect to networks.. but when I upgraded to 2.6.33-23 kernel (from 2.6.33-21) i cannot connect to networks! I can scan them but I cannot connect to them. I think I should mention that I am trying to connect to WEP networks, I havent tried wpa/open. Please don't tell me I should try to connect to open/wpa wlans because I am not in position to do that right now. 
Btw, when I boot old kernel I cannot scan networks. When I tried scanning with 'sudo iwlist' I got something like resource is temporarily busy. Please help! 
thank you,
Goran

---

### Post by Entheogen on 2010-07-20
Here's dmesg log:
```
[ 7579.556505] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[ 7581.748563] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7584.172350] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7591.171622] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[ 7591.171633] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[ 7591.171638] b43-phy0: Controller RESET (DMA error) ...
[ 7591.384834] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7596.881195] b43-phy0: Controller restarted
[ 7666.184140] b43-phy0 ERROR: MAC suspend failed
[ 7680.012649] b43-phy0 ERROR: MAC suspend failed
[ 7680.344138] b43-phy0 ERROR: MAC suspend failed
[ 7680.664149] b43-phy0 ERROR: MAC suspend failed
[ 7680.996097] b43-phy0 ERROR: MAC suspend failed
[ 7681.316125] b43-phy0 ERROR: MAC suspend failed
[ 7681.648635] b43-phy0 ERROR: MAC suspend failed
[ 7681.968129] b43-phy0 ERROR: MAC suspend failed
[ 7682.300141] b43-phy0 ERROR: MAC suspend failed
[ 7682.620138] b43-phy0 ERROR: MAC suspend failed
[ 7682.952132] b43-phy0 ERROR: MAC suspend failed
[ 7685.560156] b43-phy0 ERROR: MAC suspend failed
[ 7685.880126] b43-phy0 ERROR: MAC suspend failed
[ 7686.212133] b43-phy0 ERROR: MAC suspend failed
[ 7686.532550] b43-phy0 ERROR: MAC suspend failed
[ 7686.864150] b43-phy0 ERROR: MAC suspend failed
[ 7687.196138] b43-phy0 ERROR: MAC suspend failed
[ 7687.516530] b43-phy0 ERROR: MAC suspend failed
[ 7687.848149] b43-phy0 ERROR: MAC suspend failed
[ 7688.168119] b43-phy0 ERROR: MAC suspend failed
[ 7688.500146] b43-phy0 ERROR: MAC suspend failed
[ 7691.152160] b43-phy0 ERROR: MAC suspend failed
[ 7691.736153] b43-phy0 ERROR: MAC suspend failed
[ 7692.320141] b43-phy0 ERROR: MAC suspend failed
[ 7692.904150] b43-phy0 ERROR: MAC suspend failed
[ 7693.488150] b43-phy0 ERROR: MAC suspend failed
[ 7694.072139] b43-phy0 ERROR: MAC suspend failed
[ 7694.656150] b43-phy0 ERROR: MAC suspend failed
[ 7695.240150] b43-phy0 ERROR: MAC suspend failed
[ 7695.824142] b43-phy0 ERROR: MAC suspend failed
[ 7696.408152] b43-phy0 ERROR: MAC suspend failed
[ 7696.992163] b43-phy0 ERROR: MAC suspend failed
[ 7697.576122] b43-phy0 ERROR: MAC suspend failed
[ 7698.160151] b43-phy0 ERROR: MAC suspend failed
[ 7700.064152] b43-phy0 ERROR: MAC suspend failed
[ 7706.452122] b43-phy0 ERROR: MAC suspend failed
[ 7707.036134] b43-phy0 ERROR: MAC suspend failed
[ 7707.620117] b43-phy0 ERROR: MAC suspend failed
[ 7708.204149] b43-phy0 ERROR: MAC suspend failed
[ 7708.788153] b43-phy0 ERROR: MAC suspend failed
[ 7709.372142] b43-phy0 ERROR: MAC suspend failed
[ 7709.956150] b43-phy0 ERROR: MAC suspend failed
[ 7710.540639] b43-phy0 ERROR: MAC suspend failed
[ 7711.124141] b43-phy0 ERROR: MAC suspend failed
[ 7711.708129] b43-phy0 ERROR: MAC suspend failed
[ 7712.292122] b43-phy0 ERROR: MAC suspend failed
[ 7712.876139] b43-phy0 ERROR: MAC suspend failed
[ 7713.460149] b43-phy0 ERROR: MAC suspend failed
[ 7714.044631] b43-phy0 ERROR: MAC suspend failed
[ 7714.628142] b43-phy0 ERROR: MAC suspend failed
[ 7715.212152] b43-phy0 ERROR: MAC suspend failed
[ 7715.796152] b43-phy0 ERROR: MAC suspend failed
[ 7716.380140] b43-phy0 ERROR: MAC suspend failed
[ 7716.964153] b43-phy0 ERROR: MAC suspend failed
[ 7717.548130] b43-phy0 ERROR: MAC suspend failed
[ 7718.128130] b43-phy0 ERROR: MAC suspend failed
[ 7718.712150] b43-phy0 ERROR: MAC suspend failed
[ 7719.296140] b43-phy0 ERROR: MAC suspend failed
[ 7719.880124] b43-phy0 ERROR: MAC suspend failed
[ 7720.464153] b43-phy0 ERROR: MAC suspend failed
[ 7721.048143] b43-phy0 ERROR: MAC suspend failed
[ 7721.632124] b43-phy0 ERROR: MAC suspend failed
[ 7722.216151] b43-phy0 ERROR: MAC suspend failed
[ 7722.800140] b43-phy0 ERROR: MAC suspend failed
[ 7723.384150] b43-phy0 ERROR: MAC suspend failed
[ 7723.968144] b43-phy0 ERROR: MAC suspend failed
[ 7724.552140] b43-phy0 ERROR: MAC suspend failed
[ 7725.136150] b43-phy0 ERROR: MAC suspend failed
[ 7725.720136] b43-phy0 ERROR: MAC suspend failed
[ 7726.304142] b43-phy0 ERROR: MAC suspend failed
[ 7726.888133] b43-phy0 ERROR: MAC suspend failed
[ 7727.472144] b43-phy0 ERROR: MAC suspend failed
[ 7728.056620] b43-phy0 ERROR: MAC suspend failed
[ 7728.640150] b43-phy0 ERROR: MAC suspend failed
[ 7729.224143] b43-phy0 ERROR: MAC suspend failed
[ 7729.808138] b43-phy0 ERROR: MAC suspend failed
[ 7730.268650] b43-phy0 ERROR: MAC suspend failed
[ 7730.600141] b43-phy0 ERROR: MAC suspend failed
[ 7730.920127] b43-phy0 ERROR: MAC suspend failed
[ 7731.252134] b43-phy0 ERROR: MAC suspend failed
[ 7731.572105] b43-phy0 ERROR: MAC suspend failed
[ 7731.904133] b43-phy0 ERROR: MAC suspend failed
[ 7732.224123] b43-phy0 ERROR: MAC suspend failed
[ 7732.556122] b43-phy0 ERROR: MAC suspend failed
[ 7732.904639] b43-phy0 ERROR: MAC suspend failed
[ 7735.376118] b43-phy0 ERROR: MAC suspend failed
[ 7735.764149] b43-phy0 ERROR: MAC suspend failed
[ 7736.157353] b43-phy0 ERROR: MAC suspend failed
[ 7736.612040] b43-phy0 ERROR: MAC suspend failed
[ 7737.068090] b43-phy0 ERROR: MAC suspend failed
[ 7737.524141] b43-phy0 ERROR: MAC suspend failed
[ 7789.948129] b43-phy0 ERROR: MAC suspend failed
[ 7790.336138] b43-phy0 ERROR: MAC suspend failed
[ 7790.724128] b43-phy0 ERROR: MAC suspend failed
[ 7791.112132] b43-phy0 ERROR: MAC suspend failed
[ 7791.500120] b43-phy0 ERROR: MAC suspend failed
[ 7791.888129] b43-phy0 ERROR: MAC suspend failed
[ 7792.276634] b43-phy0 ERROR: MAC suspend failed
[ 7792.664137] b43-phy0 ERROR: MAC suspend failed
[ 7793.052130] b43-phy0 ERROR: MAC suspend failed
[ 7793.440250] b43-phy0 ERROR: MAC suspend failed
[ 7795.552138] b43-phy0 ERROR: MAC suspend failed
[ 7795.884152] b43-phy0 ERROR: MAC suspend failed
[ 7796.216120] b43-phy0 ERROR: MAC suspend failed
[ 7804.760139] b43-phy0 ERROR: MAC suspend failed
[ 7826.260129] b43-phy0 ERROR: MAC suspend failed
[ 7826.832133] b43-phy0 ERROR: MAC suspend failed
[ 7827.416140] b43-phy0 ERROR: MAC suspend failed
[ 7828.000138] b43-phy0 ERROR: MAC suspend failed
[ 7828.584136] b43-phy0 ERROR: MAC suspend failed
[ 7829.168053] b43-phy0 ERROR: MAC suspend failed
[ 7829.748056] b43-phy0 ERROR: MAC suspend failed
[ 7830.332122] b43-phy0 ERROR: MAC suspend failed
[ 7830.916642] b43-phy0 ERROR: MAC suspend failed
[ 7831.500652] b43-phy0 ERROR: MAC suspend failed
[ 7832.084133] b43-phy0 ERROR: MAC suspend failed
[ 7832.668150] b43-phy0 ERROR: MAC suspend failed
[ 7833.252150] b43-phy0 ERROR: MAC suspend failed
[ 7833.836140] b43-phy0 ERROR: MAC suspend failed
[ 7834.420150] b43-phy0 ERROR: MAC suspend failed
[ 7835.004124] b43-phy0 ERROR: MAC suspend failed
[ 7835.588141] b43-phy0 ERROR: MAC suspend failed
[ 7836.172136] b43-phy0 ERROR: MAC suspend failed
[ 7836.756133] b43-phy0 ERROR: MAC suspend failed
[ 7837.340139] b43-phy0 ERROR: MAC suspend failed
[ 7837.924638] b43-phy0 ERROR: MAC suspend failed
[ 7838.508134] b43-phy0 ERROR: MAC suspend failed
[ 7839.088150] b43-phy0 ERROR: MAC suspend failed
[ 7842.000335] b43-phy0: Radio hardware status changed to DISABLED
[ 7842.320119] b43-phy0 ERROR: MAC suspend failed
[ 7842.648133] b43-phy0 ERROR: MAC suspend failed
[ 7842.648348] b43-phy0: Radio turned on by software
[ 7842.648352] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 7843.048130] b43-phy0 ERROR: MAC suspend failed
[ 7848.020360] b43-phy0: Radio hardware status changed to ENABLED
[ 7848.588314] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 8077.964089] b43-phy0 ERROR: MAC suspend failed
[ 8078.412097] b43-phy0 ERROR: MAC suspend failed
[ 8078.788099] b43-phy0 ERROR: MAC suspend failed
[ 8079.176093] b43-phy0 ERROR: MAC suspend failed
[ 8079.564627] b43-phy0 ERROR: MAC suspend failed
[ 8079.952032] b43-phy0 ERROR: MAC suspend failed
[ 8080.340094] b43-phy0 ERROR: MAC suspend failed

```

i found tutorials how to make b43 work, so I tried using it in PIO mode.. Now I don't get DMA error but I still get MAC suspend failed and i cannot connect still...

One more thing.. It appears that now I have problem with wifi in windows too. It worked fine until new linux kernel. Yeah, I know that they aren't related but now I get "WLAN Extensibility Module has stopped." in Windows out of nowhere.. I have to put laptop to sleep and wake it up to get wlan working.. i Tried restarting WLAN service and so on but no luck. Could it be that I damaged wlan module with linux drivers? (sounds crazy, i know :))

btw, I made a mistake when I said that i upgraded to 2.6.33-23, instead I upgraded to 2.6.32-23 from repos.

Edit: Monitor mode, injection as well as whole aircrack suite works fine!

---

### Post by Entheogen on 2010-07-21
bump.
i tried installing STA driver which worked for me last night but this morning i cannot connect to wep networks with STA. get this:
```
[  843.644409] wlan3: deauthenticating from 00:1f:9f:c4:c1:24 by local choice (reason=3)
[  843.666398] wlan3: authenticate with 00:1f:9f:c4:c1:24 (try 1)
[  843.672441] wlan3: authenticated
[  843.672468] wlan3: associate with 00:1f:9f:c4:c1:24 (try 1)
[  843.675397] wlan3: RX AssocResp from 00:1f:9f:c4:c1:24 (capab=0x411 status=0 aid=1)
[  843.675402] wlan3: associated
[  843.677899] ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
```

with STA and b43 drivers!

---


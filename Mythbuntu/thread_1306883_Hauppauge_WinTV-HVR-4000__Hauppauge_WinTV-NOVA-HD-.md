---
title: "Hauppauge WinTV-HVR-4000 / Hauppauge WinTV-NOVA-HD-S2 / TeVii S460"
date: 2009-10-30
forum: Mythbuntu
---

### Post by Neon Dusk on 2009-10-30
The firmware dvb-fe-cx24116.fw in Ubuntu Karmic 'linux-firmware-nonfree' package is corrupt (as it was in Ubuntu Jaunty 6 months ago)

In the log you'll see
```

dmesg | grep cx24116
[ 36.958748] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 36.958751] i2c-adapter i2c-1: firmware: requesting dvb-fe-cx24116.fw
[ 37.072039] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 43.300007] cx24116_cmd_execute() Firmware not responding
[ 43.300010] cx24116_firmware_ondemand: Writing firmware to device failed
[ 43.300020] cx24116_firmware_ondemand: Firmware upload failed
[ 43.300022] cx24116_cmd_execute(): Unable initialise the firmware
[ 44.197200] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 44.197203] i2c-adapter i2c-1: firmware: requesting dvb-fe-cx24116.fw
[ 44.199030] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 50.352007] cx24116_cmd_execute() Firmware not responding
[ 50.352011] cx24116_firmware_ondemand: Writing firmware to device failed
[ 50.352021] cx24116_firmware_ondemand: Firmware upload failed
[ 50.352022] cx24116_cmd_execute(): Unable initialise the firmware
[ 50.704699] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...

```

To get a proper working firmware file follow the instructions for extracting the firmware at [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000) or [Launchpad](https://bugs.launchpad.net/mythbuntu/+bug/363682)

N.B. The corrupt firmware was reported 6 months ago on Launchpad [here](https://bugs.launchpad.net/mythbuntu/+bug/363682). Should this of been reported elsewhere to get it fixed??

---


---
title: "Hauppauge Usb Live 2"
date: 2013-03-06
forum: Multimedia Software
---

### Post by jls on 2013-03-06
I'm having terrible problems trying to get a USB Live 2 to work. I'm using a Dell XPS 17 L702x running Ubuntu 12.04 LTS. I initially thought it was a driver issue but It would seem that the driver should be already included in the current LTS kernel. It would also seem that others have got the card working without problem. The best I've managed so far is by using vlc and all I got is no video and the briefest snatch of audio followed by silence then another snatch of audio. Checking dmesg gives a whole bunch of "cx231xx #0: UsbInterface::sendCommand, failed with status --19". I have tried various applications with no success and the grabber itself works fine under Windows. I have checked the chipset visually to make sure it hasnt been changed to a different version. lsusb was reporting it without problem but having just tried it again its not showing at all. The only thing I've changed is I've uninstalled a few of the applications I'd installed in attempt to get some output. Any help would as always be greatly appreciated as my searches are turning up nothing.

<edit> lsusb started reporting it again after reboot as ID 2040:c200 Hauppauge. If I use lsusb -v I get "Couldn't open device, some information will be missing" . I have tried it in different ports to no avail. I am tending to think its a driver issue but I'm no expert. I think I also read somewhere that pulse and alsa can conflict but I haven't been able to find that article again

---


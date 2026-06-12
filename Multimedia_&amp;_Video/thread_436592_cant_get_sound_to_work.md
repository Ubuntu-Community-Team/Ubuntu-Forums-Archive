---
title: "cant get sound to work"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by therealmkb on 2007-05-08
its common iv read i have just installed ubuntu 6.10 on a old pc i got and i cant get the sound to work i did work first time after install then after i rebooted it stoped working i persumed it was sumthing i had edit wrongly  since im new to linux and decided to just format and start again but the sound hasnt come back since on the total format and reinstall i read a few forums and i cant get it to work please help 

i heard some say do this i hope this is of some importance

mkb@mkb-linux:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b             2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev              c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Int             egrated Graphics] (rev b1)


o the sound device is a nforce mpc or mcp (thats what it states on the chip in the side of the motherboard)

---

### Post by jocko on 2007-05-08
I don't see any audio controller in your lspci output.
Are you sure you copied the complete output?
Does "lspci | grep audio" say anything?
Do you find any audio controller listed in the device manager? (system->settings->hardware information, or run hal-device-manager from a terminal)
Do you know exactly what motherboard you have?

---

### Post by therealmkb on 2007-05-08
no it weird non are listed they are on knoppix how ever wen i use alsaconf or somthing like that but that dont apear to work on ubuntu im not sure what mother board it is exacly i did look around on it with a torch but i can find the exact modle

and yes that is the full thing i get

motherboard is a microstar ms 6737 i belive

o just to let you know the pc is a packard bell

---

### Post by therealmkb on 2007-05-08
[http://www.ciao.co.uk/MSI_Socket_A_MS_6367__5409571](http://www.ciao.co.uk/MSI_Socket_A_MS_6367__5409571) bit more info [COLOR="Blue"][review]("http://www.ciao.co.uk/MSI_Socket_A_MS_6367__5409571")[/COLOR]


and with the lspci getaudio thing i got


bash: mkb@mkb-linux:~$: command not found
mkb@mkb-linux:~$ 00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b             2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev              c2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
bash: syntax error near unexpected token `('
mkb@mkb-linux:~$ 02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Int             egrated Graphics] (rev b1)
bash: syntax error near unexpected token `('

---

### Post by jocko on 2007-05-08
The only thing I know that can prevent the system from seing the sound chipset is if you have inactivated it in BIOS.

Check your bios settings (reboot the machine and press delete during the power on self test).
[You can find the manual for the motherboard here.]("http://217.110.237.67/Manuals/6367-engl%20v1.0.pdf")
Checking the manual I see that there should be settings to enable/disable "MCP AC'97 audio" and "MCP SPDIF Out".
Make sure the AC'97 audio is enabled, and if you use spdif (digital output) it should also be enabled.

Hope this helps.

---


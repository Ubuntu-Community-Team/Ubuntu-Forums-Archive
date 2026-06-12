---
title: "Toshiba Satellite P100 11.04 External Audio Jacks Not Working"
date: 2011-06-02
forum: Multimedia Software
---

### Post by arrow203 on 2011-06-02
I have a Satellite P100 running 11.04.  The audio works fine from the internal speakers.  The notebook has three external jacks - Line In, Line Out, and Headphones.  Plugging a pair of headphones into either the Line Out or Headphone jack doesn't change the status of the output at all - sound just continues to come out of the internal speakers.

Any advice on how to troubleshoot this problem?

Thanks in advance.

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by arrow203 on 2011-06-04
[http://www.alsa-project.org/db/?f=aa75d5efebfb76f868d3d50d622302ee6f41e5f4](http://www.alsa-project.org/db/?f=aa75d5efebfb76f868d3d50d622302ee6f41e5f4)

PS - Props on the fantastic data collection method!

Thanks very much

---

### Post by lidex on 2011-06-04
OK. Have you updated the bios on this machine? Please provide these terminal outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by arrow203 on 2011-06-05
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: TOSHIBA
    Version: V4.70  
    Release Date: 01/19/20092
    Address: 0xE8ED0
    Runtime Size: 94512 bytes
    ROM Size: 64 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: TOSHIBA
    Product Name: Satellite P100
    Version: Not Applicable                  
    Serial Number: 1234567890                      

Handle 0x0008, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description: HD-Audio

---


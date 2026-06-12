---
title: "Natty shuts down at too low temperature [ThinkPad]"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pourfendeur on 2011-04-20
Hello, 

ever since I upgraded kernel to 2.6.38-8 (Natty x64) my ThinkPad Z61p has been feinting at the first sight of stress (60-65C). It appears to be stable older with 2.6.35-28, holding a bit longer to up to 75C. Fan seems to be functioning properly, up to 3500rpm. Any Idea how to fix this issue?

specifications:

CPU: Centrino Duo 2Ghz (T7200)
Operating temperature: 0-100C

Laptop: Lenovo Thinkpad Z61p

sensors output:
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +127.0°C)                  
temp2:       +50.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3084 RPM
temp1:       +49.0°C                                    
temp2:       +46.0°C                                    
temp3:       +32.0°C                                    
temp4:       +95.0°C                                    
temp5:       +37.0°C                                    
temp6:           N/A                                    
temp7:       +32.0°C                                    
temp8:           N/A                                    
temp9:       +41.0°C                                    
temp10:      +56.0°C                                    
temp11:      +52.0°C                                    
temp12:          N/A                                    
temp13:          N/A                                    
temp14:          N/A                                    
temp15:          N/A                                    
temp16:          N/A 

Thanks:)

---

### Post by bapoumba on 2011-04-20
Moved to Natty.

---

### Post by Onesimus on 2011-04-20
Have you checked your BIOS settings ?  There maybe some settings in there that might be worth looking at.

---

### Post by pourfendeur on 2011-04-21
yeah, did that, but found nothing there. Haven't actually been any issue before natty, so I suppose it's reasonable to conclude it's not a hardware problem

---

### Post by dino99 on 2011-04-21
oops

---


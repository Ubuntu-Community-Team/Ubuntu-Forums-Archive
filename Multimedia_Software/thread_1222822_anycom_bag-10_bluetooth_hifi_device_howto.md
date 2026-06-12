---
title: "anycom bag-10 bluetooth hifi device howto?"
date: 2009-07-25
forum: Multimedia Software
---

### Post by itchy8me on 2009-07-25
has anyone been able to get the anycom bag-10 (bluetooth hifi device) to work with linux? i can pair it but cannot find how to stream audio from it to my desktop.

greets,
wernher

specs:
ubuntu 9.10 64-bit

---

### Post by itchy8me on 2009-07-26
anyone?

i have tried setting up a .asoundrc file for the device however using pactl to load it does not work.

this was the output of sdptool:

> Browsing 00:15:83:10:CA:69 ...
Service Name: Headset Audio Gateway
Service RecHandle: 0x10000         
Service Class ID List:             
  "Headset Audio Gateway" (0x1112) 
  "Generic Audio" (0x1203)         
Protocol Descriptor List:          
  "L2CAP" (0x0100)                 
  "RFCOMM" (0x0003)                
    Channel: 12                    
Profile Descriptor List:           
  "Headset" (0x1108)               
    Version: 0x0102                

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x10001            
Service Class ID List:                
  "Handsfree Audio Gateway" (0x111f)  
  "Generic Audio" (0x1203)            
Protocol Descriptor List:             
  "L2CAP" (0x0100)                    
  "RFCOMM" (0x0003)                   
    Channel: 13                       
Profile Descriptor List:              
  "Handsfree" (0x111e)                
    Version: 0x0105                   

Service Name: Audio Source
Service RecHandle: 0x10002
Service Class ID List:    
  "Audio Source" (0x110a) 
Protocol Descriptor List: 
  "L2CAP" (0x0100)        
    PSM: 25               
  "AVDTP" (0x0019)        
    uint16: 0x100         
Profile Descriptor List:  
  "Advanced Audio" (0x110d)
    Version: 0x0100        

Service Name: AVRCP TG
Service RecHandle: 0x10003
Service Class ID List:    
  "AV Remote Target" (0x110c)
Protocol Descriptor List:    
  "L2CAP" (0x0100)           
    PSM: 23                  
  "AVCTP" (0x0017)           
    uint16: 0x100            
Profile Descriptor List:     
  "AV Remote" (0x110e)       
    Version: 0x0100          

Service Name: AVRCP CT
Service RecHandle: 0x10004
Service Class ID List:    
  "AV Remote" (0x110e)    
Protocol Descriptor List: 
  "L2CAP" (0x0100)        
    PSM: 23               
  "AVCTP" (0x0017)        
    uint16: 0x100         
Profile Descriptor List:  
  "AV Remote" (0x110e)    
    Version: 0x0100  

---

### Post by itchy8me on 2009-07-28
okay let me express the question in a different manner, has anyone been able to setup a a2dp client on a linux box?

---

### Post by itchy8me on 2009-08-29
bump.

---


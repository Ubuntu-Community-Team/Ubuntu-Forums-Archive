---
title: "Kino en Ubuntu 12.04 si, en 10.04 aviso"
date: 2014-03-16
forum: Multimedia Software
---

### Post by padaenriqueidey on 2014-03-16
Hola buenas. En Ubuntu 12.04 puedo capturar video de cámara digital de vídeo con Kino, teniendo insertada una tarjeta capturadora de vídeo.  
 En Ubuntu 10.04, al querer capturar me aparece este mensaje de aviso: El módulo del kernel raw 1934 no se ha cargado o no hay permiso para leer o escribir en /dev/raw/1934.
 Características del pc:  
 Disco duro 60 GB Seagate Ide Ata100 7R 7200 Rpm
 Placa base Asus A7V 333
 Micro AMD Athlon 2000 Mhz + 266 Mhz 1.66 Ghz
 Tarjeta gráfica Nvidia GF4 7200 MX440 64 Mb
 Memoria Dim DDR 512 mb 333 Mhz Oem
 Memoria Dim DDR 256 mb 333 Mhz Oem
 Tarjeta de vídeo Pci Iee 1394 Firewire
 ¿ Alguna solución? Gracias.
 Saludos.

  	 	 	 	   
Hello good. In Ubuntu 12.04 I can capture digital video camcorder with Kino, having inserted a capture video card. 
In Ubuntu 10.04, when I want to capture this warning message: The raw 1934 kernel module not loaded or no permission to read or write to / dev/raw/1934. 
Features pc: 
HDD Seagate 60GB IDE ATA100 7200 Rpm 7R 
Motherboard Asus A7V 333 
Micro Mhz AMD Athlon 2000 + 1.66 Ghz 266 Mhz 
Nvidia GF4 MX440 64MB 7200 
Dim Memory 512 mb DDR 333 Mhz Oem 
Dim Memory 256 mb DDR 333 Mhz Oem 
Video card PCI 1394 Firewire Iee 
Any solution? Thank you. 
Greetings

---

### Post by padaenriqueidey on 2014-03-18
Hola compañeros. Soluciónes:
 

  Para Ubuntu 12.04:  
  En terminal:
  sudo apt-get install kino
  sudo apt-get install mjpegtools
 

 Para Ubuntu 10.04:  
 En terminal:
 sudo apt-get install kino
 sudo apt-get install mjpegtools
 Ejecutar desde la terminal de root:
 kino

Hello fellow. solutions: 

  For Ubuntu 12.04: 
  In terminal: 
  sudo apt-get install kino 
  sudo apt-get install mjpegtools 

For Ubuntu 10.04: 
In terminal: 
sudo apt-get install kino 
sudo apt-get install mjpegtools 
Run from root terminal: 
kino

---


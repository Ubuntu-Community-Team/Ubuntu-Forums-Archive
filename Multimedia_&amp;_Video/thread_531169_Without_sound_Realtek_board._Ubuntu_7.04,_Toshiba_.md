---
title: "Without sound Realtek board. Ubuntu 7.04, Toshiba satelite U305."
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by condor uruguay on 2007-08-21
Hi, i have a Toshiba satelite U305 with Realtek audio board. I tried to config the drivers (ALSA) but it didin't work.

thanks!
Condor. 
 
 PD: Sorry my english. 
 PD2: I'm new ubuntu user.

---

### Post by mohnkern on 2007-08-21
When you type:

asoundconf list


What do you get?

---

### Post by condor uruguay on 2007-08-21
mohnkern, thanks for reply.
  
  i got this:

  $ asoundconf list
  Names of available sound cards:
  Intel

  $ lspci -v 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

  Hey ! I thought i had a Realtek board, what a fool. 

 Also i try ALSAMIXER but there is an error:

alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

$ sudo apt-get install alsamixer
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete alsamixer

 How can i solve the problem?

   PD: sorry my English again...

---

### Post by mohnkern on 2007-08-23
It's recommended that you try reinstalling Alsa with the current version.  Instructions are at 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer%3A+relocation+error%3A](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer%3A+relocation+error%3A)

---

### Post by Josillo on 2007-09-14
Hola Uruguayo!

Yo tengo una Toshiba Satellite U305-S5107 y solucioné el problema del sonido instalando una versión nueva de los drivers alsamixer.  Version 1.0.15rc1.Es un "Release Candidate", lo que significa que todavía no es una versión final, pero si es muy estable.   A mi me funcionó.

Te dejo el link...

[http://ubuntuforums.org/showthread.php?p=3304073#post3304073](http://ubuntuforums.org/showthread.php?p=3304073#post3304073)


Off topic:  Hablando de sonido... anoche lo fuí a ver a Francisco Fattoruso...  :guitar:  muy bueno.  Encima lo trajo a Tony Royster Jr en la batería.... un animal.


I hope it's okay if I post in spanish here.  All I mentioned is the link where he can find a solution for this problem, and some off topic comment about music.

Cheers!


Josillo

---


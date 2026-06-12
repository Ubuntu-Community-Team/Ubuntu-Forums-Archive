---
title: "Sintonizadora de TV Kozumi"
date: 2013-04-10
forum: Multimedia Software
---

### Post by damidami on 2013-04-10
Hi,
I have the kozumi tv tuner card, and I'm trying to make it works in ubuntu.
The worst thing is that I already made it work (I could see and listen channels ok), but then I spoiled the whole thing and don't know how to fix it.

At first I tried with tvtime, I managed to see images but very blurry even if I setted it to Pal-nc that is the one in my country (argentina).  And I could listen the audio.
Then I tried with xawtv, there I managed to see the image clearly, but the audio was too low, I downloaded alsamixer and I managed to turn the volume up in the rear mic, that is where the sound cable from the kozumi card enters.

And there everything was working fine.  But every time I opened xawtv I had to set pal-nc (it defaulted to ntsc) and frequency us-cable (I don't know wich came default), so I decided to make a config file .xawtv
I copied the example file from this page [http://linux.die.net/man/5/xawtvrc](http://linux.die.net/man/5/xawtvrc)
(and changed only the paremeters to set pal-nc and us-cable)

When I opened xawtv after that, I could see only one channel and it didn't let me change it, and I had lost the audio.  I tried to remove the .xawtv file and reboot the machine, but now it doesn't let me see any channel.
In the capture device it says Composite0 (and if I'm not mistaken it used to say "Television" but now that option is gone)

What can I do now? Any ideas? Thanks in advance for any help!

-----

Hola,
Tengo la sintonizadora de tv kozumi, y estoy intentando hacerla andra en ubuntu.
La peor parte es que en un momento lo logré (se veía y escuchaba bien) y después lo arruiné todo y no se como arreglarlo.

Al principio probé con el tvtime, logré ver imágenes pero bastante borrosas incluso seteando pal-nc que es el de mi pais (argentina).  Y no se escuchaba el audio
Luego probé el xawtv, ahí logré que se viera perfecto pero el volumen estaba muy bajo, me bajé el alsamixer y logré subirle el volumen al micrófono (rear-mic) que es por donde entra el sonido con un cable desde la capturadora kozumi.  

Y ahí estaba andando todo bien.  Pero cada vez que entraba al xawtv tenía que setear pal-nc (por default venía ntsc), y la frecuencia us-cable (no se cual venía), entonces quize crear un archivo de configuración .xawtv
Copié el archivo de configuración de esta página: [http://linux.die.net/man/5/xawtvrc](http://linux.die.net/man/5/xawtvrc)
(y le cambié solamente los parámetros para setear pal-nc y us-cable)

Al iniciar xawtv sólamente me mostraba un canal y no me dejaba cambiarlo, y había perdido el sonido.  Probé borrar el archivo de configuración y resetear la máquina, pero ahora no me deja ni siquiera ver ningún canal.
En el dispositivo de captura aparece Composite0 (y si no mal recuerdo antes aparecía Television, pero ahora no aparece).

Que puedo hacer? Gracias por su ayuda!

---


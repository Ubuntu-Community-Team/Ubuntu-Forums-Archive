---
title: "Problemas con dependencias de Paquete"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by cbueno1973 on 2007-12-12
Hola Gente:
                Instalé hace dos semanas ubuntu 7.10, venía más o menos bien. Estaba teniendo problemas con los codecs, como casi todos.
              El otro dia desapareció del menú **Totem **( seguramente debe tener que ver con las actualizaciones y conflictos de paquetes )
             Es tal así el problema que ahora solo tengo como reproductor por default cuando hago doble click con un archivo mp3 **Rhytmbox Music Player**.
 Este mensaje sigue confirmando el error cuando intento instalar el mplayer y tengo el siguiente error.
Tras escribir el siguiente comando en un terminal:

**sudo apt-get install mplayer**

**Error**
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libpulse0 but it is not installable
           Depends: libungif4g (>= 4.1.4) but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages

---

### Post by ImALittleTeaPot on 2007-12-12
4

---


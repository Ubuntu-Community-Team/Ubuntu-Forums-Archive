---
title: "Problemas con resolución de pantalla en Ubuntu 14.04"
date: 2015-01-06
forum: Multimedia Software
---

### Post by XAiker on 2015-01-06
Al igual que en el post "http://ubuntuforums.org/showthread.php?t=2222919" no puedo cambiar de resolucion que no sea 640x480. E seguido todos loas pasos de ese post y nada, al crear el doumento "xorg.conf" se me bugea completamente el SO, y tengo que reinstalar Ubuntu 14.04. Ayuda por favor.

---

### Post by papibe on 2015-01-06
Hola XAiker.

Recuerda que puedes pasarte a modo texto, y de ahí puedes borrar o editar el xorg.conf. Puedes hacer esto presionando las teclas Ctrl+Alt+F1

En ese mismo ambiente puedes resetear la máquina si ejecutas:
```
sudo reboot
```
Empezemos viendo que tarjeta gráfica, tienes, que driver estás usando, etc.  Puedes abrir un terminal, ejecutar estos comandos y responder con los resultados (puedes copiar y pegar el texto del terminal)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'

xrandr -q 

xrandr -q --q1

[ -f /etc/X11/xorg.conf ] && cat -n /etc/X11/xorg.conf
```

Saludos.

---

### Post by XAiker on 2015-01-06
Me sale esto: 
```

"01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 525M] [10de:0dec] (rev a1)
    Subsystem: Toshiba America Info Systems Device [1179:fc50]
01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
xaiker@xaiker-SATELLITE-L755:~$ 
xaiker@xaiker-SATELLITE-L755:~$ lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
xaiker@xaiker-SATELLITE-L755:~$ 
xaiker@xaiker-SATELLITE-L755:~$ xrandr -q 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480        73.0* 
xaiker@xaiker-SATELLITE-L755:~$ 
xaiker@xaiker-SATELLITE-L755:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0    640 x 480    ( 169mm x 127mm )  *73  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
xaiker@xaiker-SATELLITE-L755:~$ 
xaiker@xaiker-SATELLITE-L755:~$ [ -f /etc/X11/xorg.conf ] && cat -n /etc/X11/xorg.conf"

```
Gracias

---

### Post by papibe on 2015-01-06
Gracias.

Tu caso es un poco diferente. Tu tienes una tarjeta Nvidia. No uses el xorg.conf de la otra conversación.

No pude ver si estás usando el driver proprietario de Nvidia. Trataste de instalarlo?

Si no, te recomiendo instalarlo ya que podría resolver tus problemas. Abre 'Additional Drivers' (o el equivalente en español) e instala el driver que te ofrece el sistema. Después re inicializa tu computadora y cuéntanos como te va.

Saludos.

---

### Post by XAiker on 2015-01-06
Cambie al que tenia la vercion mas nueva, no paso nada asi que reinicie para ver si se aplicaban los cambios despues de reiniciar, no me carga el controlador de video, osea me queda la pantalla negra, sin puntero ni nada, osea ubuntu me carga pero al momento de cargar el escritorio se me queda todo negro. Ya me habia pasado antes. Quizas si modificl el archivo "xorg.conf" desde el controlador de video default funcione, pero no tengo ni idea de como es la configuracin xorg.conf para mi PC.
Gracias

---

### Post by papibe on 2015-01-06
Me gustaría ver la bitácora (log) de xorg.

Puedes por favor pegar el contenido de este archivo:
```
/var/log/Xorg.0.log
```
en esta página web [http://paste.ubuntu.com/](http://paste.ubuntu.com/) y después postear el link al archivo?

Saludos.

---

### Post by XAiker on 2015-01-06
Siento demorar tato pero tenia que reinstalar Ubuntu.
Me sale "bash: /var/log/Xorg.0.log: Permission denied"

gracias

---

### Post by papibe on 2015-01-06
No lo ejecutes, es un archivo de texto.

Copia el contenido del archivo.

Gracias.

---

### Post by XAiker on 2015-01-06
Lo siento! No me di cuenta! 
[http://paste.ubuntu.com/9684605/](http://paste.ubuntu.com/9684605/)
gracias

---

### Post by papibe on 2015-01-06
Gracias.

Pareciera que driver de Nvidia no estuviera instalado.

Puedes responderme cual es el resultado de este comando?
```
dpkg -l | grep nvidia
```
Saludos.

---

### Post by XAiker on 2015-01-06
No pasa absolutamente nada, solamente me aparece para introducir otro comando, nada mas, como si itroducciera un comando que no hiciera nada

---

### Post by papibe on 2015-01-06
Ok.

Instalemos el driver entonces:
```
sudo apt-get install nvidia-current
```
Si todo sale bien, reinicia y cuéntame como te va.

Si todavía hay problemas, por favor vuelve a pegar el archivo anterior (/var/log/Xorg.0.log) para ver que error tenemos ahora.

Saludos.

---

### Post by XAiker on 2015-01-06
Se me creo un archivo aparte que se llama Xorg.0.log.old
[http://paste.ubuntu.com/9684878/](http://paste.ubuntu.com/9684878/)
Gracias

---

### Post by papibe on 2015-01-06
Que tal lo demás? Instalaste el driver?  Que pasó cuándo reseteaste?

El archivo se genera cada vez que se inicializa el modo gráfico, por lo tanto aunque tenga el mismo nombre, el contenido es distinto después de cada inicialización.

Saludos.

---

### Post by XAiker on 2015-01-07
Cuandon reinicie la PC no me inicio mas el sistema, osea me carga el sistema, pero cuando me tiene que pedir la contraseña queda la pantalla en negra, la deje 2 horas pero no hay caso, tuve que reinstalar Ubuntu, por eso la demora. Lo mas gracioso es que cuando inicio con el live CD osea con el Wubi la resolucion de la pantalla es de "1080 x 720" puero despues de instalado el sitema se me cambia automaticamente "640x480". Hay algo mas pra probar o ya no tiene remedio? Mi pc antes tenia ubuntu hace unos 6 o 7 meses y me tiraba las resluciones que yo queria, pero ahora no se.
Muchas gracias

---


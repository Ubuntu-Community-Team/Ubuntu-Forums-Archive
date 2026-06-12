---
title: "Sin Audio: Placa Asus M2N-MX SE Serie X"
date: 2009-03-06
forum: Multimedia Software
---

### Post by Eddie-Z on 2009-03-06
Después de usar por muchos años Window, por fin decidí pasarme a linux Ubuntu. Solo que hasta ahora no puedo escuchar correctamente el Audio. Mi placa es AM2, Nvidia nForce 430 MCP. Solo escucho un sonido leve y en solo uno de los parlantes. En el woofer también se escucha un sonido muy bajo e ilegible. Ya intente por todos los medios configurar el audio, sin resultado alguno. Sería alguien tan amable de darme una ayuda.

;)

Desde ya, muchas gracias.

---

### Post by avrilrox on 2009-03-06
Probaste con alsamixer?

```
alsamixer
```


De casualidad estas usando el Chip C-Media 6501? Hace como cuatro dias que lo logre hacer andar.

Si tenes el mismo chip, hace esto:

1.Tenes que editar el archivo de modulos de Alsa:

```
sudo gedit /etc/modprobe.d/alsa-base
```+

Edita la linea

```
options snd-usb-audio index=-2
```

a

```
options snd-usb-audio index=0
```

2. Cambia todo a ALSA en Sistema -> Preferencias -> Sonidos.

Deja seleccionado como mixers Speaker y Speaker 1(si te aparece).

3. Asegurate de tener alsa 1.0.14 o mas reciente.

4. Create un archivo .asoundrc en tu home y pega lo siguiente:

```
 pcm.!dmix {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0" #Aqui puede ser hw:x,y donde "x" es el dispositivo e "y" el subdispositivo
channels 8 #Esto depende de tus parlantes puden ser 6 (5.1) u 8 (7.1) canales
period_size 1024
buffer_size 8192 #Si no te funciona usa un numero menor

}
}
pcm.!default {
type plug
slave.pcm "dmix"
slave.channels 8
route_policy duplicate
} 

```

---

### Post by Eddie-Z on 2009-03-07
Muchas gracias avrilrox por tu respuesta... No entiendo mucho sobre hardware, pero fijandome en el manual de mi placa dice: Chipset NVIDIA nForce 430/GeForce6100...

Pregunto: ¿funcionará en dicho chipset la sugerencia que me has dado?

Desde ya muchas gracias, de nuevo... Estaré atento a cualquier otro detalle.

Saludos

---


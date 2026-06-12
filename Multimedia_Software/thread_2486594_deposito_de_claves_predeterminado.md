---
title: "deposito de claves predeterminado"
date: 2023-05-05
forum: Multimedia Software
---

### Post by adrian1234 on 2023-05-05
Hola. 

Soy nuevo en Linux Ubuntu 22.04 LTS y me encuentro con una gran dificultad que no consigo arreglar. Cuando inicio el PC, sin hacer nada acaba apareciendo en pantalla el siguiente mensaje: Se necesita autenticación Una aplicación quiere acceder al depósito de claves depósito de claves predeterminado, pero está bloqueado (imagen adjunta).

No me deja introducir ningún carácter, ni cancelar ni nada de nada de nada.

A los pocos segundos se pone toda la pantalla en negro con unas letras de colores de ubuntu, y murió. He de reiniciar el pc de nuevo y vuelta a lo mismo.

Lo más lejos que he conseguido llegar cuando se inicia el pc es:

1.Accede a una terminal presionando las teclas Ctrl+Alt+F2.
2. Ingresa tu nombre de usuario y contraseña cuando la terminal te solicite.

A partir de aquí no sé avanzar y por más que busco por internet cosas no consigo desbloquear o eliminarlo. Antes de hacer un reboot quería pedir ayuda aquí.

Encontré una info que me decía lo siguiente, pero el punto 3 no funciona. Imagen adjunta más abajo. He probado otras cosas que he encontrado por internet, pero tampoco funciona.
3. Ingresa el siguiente comando para eliminar el depósito de claves:
 
          rm ~/.local/share/keyrings/login.keyring
 
4. Reinicia el sistema ingresando el comando:
 
          sudo reboot

Muchas gracias de antemano, espero que alguien me pueda ayudar a quitar ese mensaje y seguir utilizando Linux que con tanta ilusión y ganas tenia antes de iniciar esta aventura con Ubuntu.

¡Gracias!

Adrián.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292178&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292179&stc=1[/IMG]

---


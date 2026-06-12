---
title: "Problem hosting website: &quot;Requested URL was not found on this server&quot;"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by VotaVader on 2010-11-21
Hi,

For a university course, I'm doing an upgrade of a web based application for a charity organization. To test the changes that we're making to the code, I wanted to set up a server on my home PC to host a copy of the site. I've configured apache, php and mysql like the server that's currently hosting the real app, but I have a problem:

The first page is a login screen. This, of course, has a login form like so:

```
<form id="login" action="/menu/login" method="post"> 
	<fieldset class="a_cuatrocincuenta">
           <legend>
	     <ol>  
	       <li>
		 <label for="email_address">Usuario:</label> 
		 <input name="data[FormLogin][nom_login]" value=""/>								       </li>

	       <li>
	         <label for="password_field">Contrase&ntilde;a:</label> 
		 <input type="password" name="data[FormLogin][pas_voluntario]"  size="20" maxlength="255" value="" id="FormLoginPasVoluntario" />					 
	       </li>
	     </ol>
           </legend>
	 </fieldset>
	 <fieldset class="submit">
            <legend><input type="submit" value="Entrar" /></legend>
	 </fieldset>
      </form>  
```

As you can see, the action for the form is supposed to be the directory /menu/login. The problem is that there is no such directory under the webroot directory of the app. Evidently when I try to log in through this form, I get the Apache error "The requested URL /menu/login was not found on this server". I checked on the original server (I have access to it through ssh) and the code is exactly the same, but it works. There are no extra symlinks that I'm not following either. I don't understand.

To make it clear, this app was programmed by other people (that's why I don't understand the code), it was done on php with the Cake framework. Maybe that has something to do with it... does anyone know how this can be possible or how this can occur?

Thanks for any advice, this has been driving me crazy, and we still can't test anything.](*,)

---

### Post by VotaVader on 2010-11-21
Bump? Anyone? Please?

---

### Post by ironic.demise on 2010-11-21
On the "real" server, is there a /menu/login directory or file?
If there is, copy it over into your server directory, if not I can't see why it wouldn't get the error, yet you do?

---

### Post by VotaVader on 2010-11-21
Well, there is a directory called menu in the app directory, and it has a login.thtml file inside, but it's not under the webroot directory. That seems to be fine since the application doesn't seem to do much from the actual webroot directory (it just defines the locations of the app directory and root directory, and that's why I thought it might have been a symbolic link problem at first), and it seems to access the script that loads the login screen fine. But I don't know from which directory it then tries to access /menu/login. Still, it seems to be a directory access and not a .thtml file access, and there is no login directory anywhere.
On the real server there is no symbolic link to that menu directory from the webroot directory, and the files on my computer (test server) are exactly copied from there. That's why I find it really strange that it works on that server...

---

### Post by ironic.demise on 2010-11-21
Did you copy the Apache setup files?

---

### Post by VotaVader on 2010-11-21
Not exactly. I don't have root access, and I can't find the apache folder under /etc so I assume I don't have the privileges to view those directories. Could there be something special on the apache config? I just set the root directory of apache to the webroot directory of the app, and that loaded the login screen fine...

---

### Post by ironic.demise on 2010-11-22
Is there no way you could gain root?
LiveCD or sudo?

The problem "may" be in an Apache configuration...
Unless I knew more about the server I couldn't say for sure.

Have you gotten the login screen working yet?

---

### Post by SeijiSensei on 2010-11-22
I'd bet the virtualhost definition includes an Alias directive pointing to the server's /menu/login directory.  Try adding this to the <VirtualHost> container in your local Apache configuration:

```
Alias /menu/login /path/to/menu/login
```

replacing "/path/to/menu/login" with the actual file path on your machine.  If that doesn't work properly, try aliasing just "/menu" instead.

---

### Post by VotaVader on 2010-11-23
It was in fact the apache configuration. The server used an old version of httpd and I was not loading all the necessary modules on apache startup (specifically to the login problem, the mod_rewrite module). I finally resorted to XAMPP which had a similar config as the old httpd from the server, and I finally got past the problem... now to deal with the MySQL connection. Thanks for all the input guys!

---


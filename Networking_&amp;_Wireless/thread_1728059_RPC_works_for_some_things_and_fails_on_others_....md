---
title: "RPC works for some things and fails on others ..."
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by Bendb on 2011-04-13
Hello,

I'm trying to use a remote procedure call. When I call my server, my server should activate gammu and send an sms with it.
I've used the code in the following tutorial:
[http://www.devshed.com/c/a/PHP/Using-XMLRPC-with-PHP/](http://www.devshed.com/c/a/PHP/Using-XMLRPC-with-PHP/)

The command for the uptime, and the command for the greeting work perfectly.
But when i write my own method on my server, it fails ..
```
function uptime_func($method_name, $params, $app_data) { return `uptime`; } function greeting_func($method_name, $params, $app_data) { $name = $params[0]; return "Hello, $name. How are you today?"; }
function gammu_func($method_name, $params, $app_data)
{
$text = $params[0];
$number = $params[1];
$result = "echo '$text' | gammu sendsms TEXT $number";
exec("$result");
return $result;
}
```

On my Client (the one that calls the server) i see the output of $result. So my gammu_func is definitely working... He just doesn't execute ```
 exec("$result")
```

I know that syntax is right cause i tried it in a different php file. I think it has something to do with the user rights.
I don't think I have the priviliges to run that command ...

Does anyone have a clue about what to do here?

Thanks for the replies!

Ben

---

### Post by Bendb on 2011-04-14
Ok,

Still looking for the solution but i'm getting a lot closer to it! :)
I found out that the user www-data runs the RPC commands. But he isn't able to run the exec() command to send a gammu sms.
I've set everything up to be able to run exec() commands, and now this works too.

The only problem i have now is that the user www-data isn't allowed to use gammu.
I tried a lot of things, but still no luck.
The output of gammu is:
```

Warning: No configuration file found!
Warning: No configuration file read, using builtin defaults!
Error during reading from the device.

```

This means that the user www-data can't read the config file. Cause he's not permitted to do so.

I did the following things:

-in /etc/sudoers
```

www-data ALL=NOPASSWD:/usr/bin/gammu
www-data ALL=NOPASSWD:/usr/bin/gammu-config
www-data ALL=NOPASSWD:/bin/bash
www-data ALL=NOPASSWD:/bin/sh

```

-added www-data to the dialout group. (Able to communicate with the device now).

-Copied the gammu config file to a path where www-data should reach (not sure if it does now :()

Any more suggestions?

Thanks!

---

### Post by Bendb on 2011-04-14
Found it! 

I copied the gammu config file, but i didn't change the permissions of it. So www-data couldn't read it.

Now everything works smoothly ;)

---


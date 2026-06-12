---
title: "Mythweb Server Error 500"
date: 2013-04-22
forum: Mythbuntu
---

### Post by Hishighness on 2013-04-22
Hey all, I'm wondering if someone can help me fix my mythweb. Everything else about MythTV works fine but every time I try to get to mythweb I get a Server Error 500 message. I've used apache and mysql before but not to the extent where I can troubleshoot something like this on my own.

Is there a log or something I can pass along to get the ball rolling? I'm running Ubuntu 12.10 and MythTV 0.25

Edit: Forgot to mention I can surf to other pages on my local apache server fine.

Thanks for your time,
H2

---

### Post by PhilWig on 2013-04-23
You have set:

Mythtv Control centre > plugins > mythweb enabled

Mythtv Backend setup > General > Host address Setup > Local and Master IP addresses
   -  Set both to backend server address.  
This address will need to be static or always set the same by your router/DHCP server. 

Phil

---

### Post by Hishighness on 2013-04-24
I believe that's already done, unless I did it wrong. Here are the screenshots of each just in case.

Control Center ->[http://img593.imageshack.us/img593/444/workspace1093.png](http://img593.imageshack.us/img593/444/workspace1093.png)

Backend-> [http://img823.imageshack.us/img823/9733/workspace1089.png](http://img823.imageshack.us/img823/9733/workspace1089.png)

Edit: I hadn't had password protect on before, I turned it on and when I surfed to Mythweb it asked me for the username/password but then when I entered it I still got the 500 error.

---

### Post by tgm4883 on 2013-04-24
You'll want to look at the apache logs. They should be in /var/log/apache/  I don't recall if there is a specific one for mythweb or mythtv in that directory, so you'll need to see what is in there. Post the error logs here and we can take a look.

---

### Post by Hishighness on 2013-04-25
error.log
```
[Thu Apr 25 07:38:22 2013] [error] [client 127.0.0.1] PHP Warning:  Unknown: function '0' not found or invalid function name in Unknown on line 0[Thu Apr 25 07:38:23 2013] [error] [client 127.0.0.1] PHP Fatal error:  Call-time pass-by-reference has been removed in /usr/share/mythtv/bindings/php/MythBase.php on line 50
[Thu Apr 25 07:38:24 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
```

access.log
```
127.0.0.1 - - [25/Apr/2013:07:38:16 -0300] "GET /mythweb/ HTTP/1.1" 401 746 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31"127.0.0.1 - username [25/Apr/2013:07:38:22 -0300] "GET /mythweb/ HTTP/1.1" 500 411 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31"
127.0.0.1 - - [25/Apr/2013:07:38:24 -0300] "GET /favicon.ico HTTP/1.1" 404 499 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31"
```

And here's /usr/share/mythtv/bindings/php/MythBase.php
[PHP]<?php/**
 *  This is the base object to handle all the common features for all myth classes
 *
 * @license     GPL
 *
 * @package     MythWeb
 * @subpackage  Classes
 *
/**/


class MythBase {
    public $cacheKey = null;
    public $cacheLifetime = 600;
    private static $instances = array();


    public static function &find() {
        $class = get_called_class();
        $args = func_get_args();
        $key = self::getCacheKey($class, $args);
        if (is_null($key)) {
            $r = new ReflectionClass($class);
            $obj = $r->newInstanceArgs($args);
            return $obj;
        }
        elseif (!isset(self::$instances[$key])) {
            self::$instances[$key] = &Cache::getObject($key);
            if (is_null(self::$instances[$key]) || !is_object(self::$instances[$key]) || get_class(self::$instances[$key]) !== $class) {
                $r = new ReflectionClass($class);
                self::$instances[$key] = $r->newInstanceArgs($args);
                self::$instances[$key]->cacheKey = $key;
            }
        }
        return self::$instances[$key];
    }


    public function clearCache() {
        if (!is_null($this->cacheKey))
            return Cache::delete($this->cacheKey);


        $key = $this->getCacheKey();
        if (!is_null($key))
            return Cache::delete($key);


        return false;
    }


    public function __destruct() {
        if (!is_null($this->cacheKey))
            Cache::setObject($this->cacheKey, &$this, $this->cacheLifetime);
        $this->cacheKey = null;
    }


    public function __wakeup() {
        if (!is_null($this->cacheKey)) {
        // Prevent multiple cache writes for a single key
            if (isset(self::$instances[$this->cacheKey]))
                self::$instances[$this->cacheKey]->cacheKey = null;
            self::$instances[$this->cacheKey] = &$this;
        }
    }


    private static function getCacheKey(&$class = null, &$data = null) {
        if (is_null($class)) {
            $class = get_called_class();
            $data = &$this;
        }
        elseif (is_object($class)) {
            $data =& $class;
            $class = get_class($data);
        }


        switch ($class) {
            case 'Program':
                if (isset($data[0]['chanid']))
                    $ret = implode(',', array('chanid'=>$data[0]['chanid'], 'starttime'=>$data[0]['starttime']));
                elseif (isset($data['chanid']))
                    $ret = implode(',', array('chanid'=>$data['chanid'], 'starttime'=>$data['starttime']));
                elseif (isset($data[4]) && isset($data[10]))
                    $ret = implode(',', array('chanid'=>$data['4'], 'starttime'=>$data['10']));
                else
                    return null;
                break;
            case 'Channel':
                if (isset($data['chanid']))
                    $ret = $data['chanid'];
                elseif (isset($data[0]))
                    $ret = $data[0];
                else
                    return null;
                break;
            case 'Translate':
                $ret = '';
                break;
            case 'Schedule':
                if (is_null($data) || is_object($data))
                    return null;
                $ret = implode(',', $data);
                break;
            default:
                $ret = implode(',', $data);
                break;
        }
        return "$class($ret)";
    }


}[/PHP]

---

### Post by tgm4883 on 2013-04-25
Are you using an up to date version of mythtv? ( I see you are on 0.25, but the Mythbuntu developers have a 0.25+fixes repo that you can activate in the Mythbuntu Control Centre )

---

### Post by cpeters on 2013-05-05
> **Hishighness said:**
> Hey all, I'm wondering if someone can help me fix my mythweb. Everything else about MythTV works fine but every time I try to get to mythweb I get a Server Error 500 message. I've used apache and mysql before but not to the extent where I can troubleshoot something like this on my own.

Is there a log or something I can pass along to get the ball rolling? I'm running Ubuntu 12.10 and MythTV 0.25
H2

You can probably find errors about the php memory in your apache error logs.

Look in /etc/apache2/sites-enabled/mythweb.conf and find the section with php_value memory_limit.  The default is set to 64M and the file shows other options, so comment out the 64MB line and uncomment one of the others.  I enabled 512MB, but I have rather large myconverg database.  My uncompressed DB backup is 697M, and growing.

---


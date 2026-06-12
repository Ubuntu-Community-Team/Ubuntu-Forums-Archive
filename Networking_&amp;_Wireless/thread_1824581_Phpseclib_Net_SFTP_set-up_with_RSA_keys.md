---
title: "Phpseclib Net_SFTP set-up with RSA keys"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by txheat on 2011-08-14
I need to set up SFTP using a public key without a password from within PHP on Ubuntu, but I can't get the script to work.

To make sure that sftp is even possible, I set it up to work from the bash prompt and it works well, so that's out of the way.

I installed the phpseclib Net_SFTP and Crypt_RSA packages following the phpseclib documentation, and below is my script. To simplify testing, the public key file "id_rsa.pub" and private key file "id_rsa" (generated when I set up sftp from the shell) reside in the same directory as my test script:

////////////////////////////////////////////////

set_include_path(get_include_path() . PATH_SEPARATOR . 'phpseclib');
include_once('Net/SSH2.php');
include_once('Net/SFTP.php');
include_once('Crypt/RSA.php');
include_once('Crypt/Hash.php');
include_once('Math/BigInteger.php');

$rsa = new Crypt_RSA();
//$pubKey = file_get_contents('id_rsa.pub');
//$rsa->setPublicKey($pubKey);
$priKey = file_get_contents('id_rsa');
$rsa->loadKey($priKey);

$sftp = new Net_SFTP('myremoteserver');
//if (!$sftp->login('myusername', $password)) {
if (!$sftp->login('myusername', $rsa)) {
    exit("Login Failed\n");
}
echo $sftp->pwd() . "\r\n";
$sftp->put('filename.ext', 'Hello, world!');

////////////////////////////////////////////////

The script works if I use a string password (commented out above), but when I use the $rsa object, the script fails. I tried setting the public key (commented out above) but that fails, too.

Any thoughts on what I'm missing or doing wrong? Thanks!

---

### Post by nickleboyblue on 2011-08-14
You may want to check out the PHP irc channel and post a link to your post here when you get someone to agree to look at it.

I too would be interested in seeing how this is done.

---

### Post by yawnmoth on 2011-08-14
Maybe the private key is password protected?

Is the private key one you could share?  Or could you share a similarly formatted key?

---

### Post by txheat on 2011-08-15
I generated the keys as follows -- output paths and values are for illustration only, but the prompts are real:

$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/myhome/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /myhome/.ssh/id_rsa.
Your public key has been saved in /myhome/.ssh/id_rsa.pub.
The key fingerprint is:
ab:cd:ef:01:23:45:67:89:ab:cd:ef:gh:17:65:ca:6e myid@myserver

As shown, the keys were generated WITHOUT a passphrase. The private and public key file permissions are 600, and the sftp script is run as the file owner. The public key was also placed in the .ssh directory of the remote server, and this allowed sftp to work automatically from the bash prompt. Now if we can just get it to work from within PHP using phpseclib...

---

### Post by yawnmoth on 2011-08-18
> Is the private key one you could share? Or could you share a similarly formatted key? 
Also, what happens if you do chmod 777 on the file?

Maybe you're thinking phpseclib doesn't support the key format or that it's support of it is broken but I don't believe that's the case, given posts like this:

[http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=22693](http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=22693)
[http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=21020](http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=21020)
[http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=15226](http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=15226)

All of those posts are saying that phpseclib's RSA key parsing works, save for under very specific conditions.  None-the-less, it's hard to say anything for sure about phpseclib's ability to parse the key without having an identically formatted key.

Finally, why are you posting here and not the phpseclib support forums?  Seems like you might get better support there than here.

---


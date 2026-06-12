---
title: "is there a command line tool to flip a line of text with..."
date: 2012-10-30
forum: Multimedia Software
---

### Post by shantiq on 2012-10-30
....    then copy and paste into a text document?   to flip it upside down    a vertical flip?


**answer is**   and thanx to Lars Noodén for script



```
#!/usr/bin/perl

use strict;
use warnings;
use utf8;

binmode(STDOUT, ":utf8");

my %flipTable = (
    "a" => "\x{0250}",
    "b" => "q",
    "c" => "\x{0254}", 
    "d" => "p",
    "e" => "\x{01DD}",
    "f" => "\x{025F}", 
    "g" => "\x{0183}",
    "h" => "\x{0265}",
    "i" => "\x{0131}", 
    "j" => "\x{027E}",
    "k" => "\x{029E}",
    "l" => "|",
    "m" => "\x{026F}",
    "n" => "u",
    "o" => "o",
    "p" => "d",
    "q" => "b",
    "r" => "\x{0279}",
    "s" => "s",
    "t" => "\x{0287}",
    "u" => "n",
    "v" => "\x{028C}",
    "w" => "\x{028D}",
    "x" => "x",
    "y" => "\x{028E}",
    "z" => "z",
    "A" => "\x{0250}",
    "B" => "q",
    "C" => "\x{0254}", 
    "D" => "p",
    "E" => "\x{01DD}",
    "F" => "\x{025F}", 
    "G" => "\x{0183}",
    "H" => "\x{0265}",
    "I" => "\x{0131}", 
    "J" => "\x{027E}",
    "K" => "\x{029E}",
    "L" => "|",
    "M" => "\x{026F}",
    "N" => "u",
    "O" => "o",
    "P" => "d",
    "Q" => "b",
    "R" => "\x{0279}",
    "S" => "s",
    "T" => "\x{0287}",
    "U" => "n",
    "V" => "\x{028C}",
    "W" => "\x{028D}",
    "X" => "x",
    "Y" => "\x{028E}",
    "Z" => "z",
    "." => "\x{02D9}",
    "[" => "]",
    "'" => ",",
    "," => "'",
    "(" => ")",
    "{" => "}",
    "?" => "\x{00BF}", 
    "!" => "\x{00A1}",
    "\"" => ",",
    "<" => ">",
    "_" => "\x{203E}",
    ";" => "\x{061B}",
    "\x{203F}" => "\x{2040}",
    "\x{2045}" => "\x{2046}",
    "\x{2234}" => "\x{2235}",
    "\r" => "\n",
    " " => " "
);

while ( <> ) {
    my $string = reverse( $_ );
    while ($string =~ /(.)/g) {
	print $flipTable{$1};
    }
    print qq(\n);
}
```


save as flip.pl   in your home folder


then

```
sudo mv flip.pl /bin/
cd /bin/
sudo chown yourusername flip.pl && sudo chmod +x flip.pl

```


then open terminal    enter    ```
flip.pl
```

write what you want   and enter     
copy and paste wherever you want   text document or internet forum etc...


                                          &#633;&#477;&#647;u&#477; pu&#592; &#647;u&#592;&#653; no&#654; &#647;&#592;&#613;&#653; &#477;&#647;&#305;&#633;&#653;
&#729;&#729;&#729;&#596;&#647;&#477; &#623;n&#633;o&#607; &#647;&#477;u&#633;&#477;&#647;u&#305; &#633;o &#647;u&#477;&#623;n&#596;op &#647;x&#477;&#647; &#647;u&#592;&#653; no&#654; &#633;&#477;&#652;&#477;&#633;&#477;&#613;&#653; &#477;&#647;s&#592;d pu&#592; &#654;do&#596;
[B]


==================[/B]


if you want to reverse back to front


write your text in text editor   save as   mytext to home folder

then enter


```
rev mytext
```    copy and paste the result   tluser eht etsap dna ypoc

and  of course you can combine both for truly cryptic results      &#596;od&#654; &#592;up d&#592;s&#647;&#477; &#647;&#613;&#477; &#633;&#477;sn&#643;&#647;

---

### Post by papibe on 2012-10-30
Hi shantiq.

Graphically or reverse line order?

Regards.

---

### Post by shantiq on 2012-10-30
hi papibe the second line here   i did this with [http://www.typeupsidedown.com/](http://www.typeupsidedown.com/) but want to do it in ubuntu and command line if poss


What happened to the cross- eyed circumcisor ?

 &#670;&#596;&#592;s &#477;&#613;&#647; &#647;o&#387; &#477;&#613;



sorry about the joke

---

### Post by papibe on 2012-10-30
:D That is a neat trick.

Unfortunately the closest thing I know would be 'tac' and 'rev'.

Regards.

---

### Post by jmull on 2012-10-30
The code is in the source for that page. It's not really complex so you should be able to convert it something that can be executed on the command line.

---

### Post by shantiq on 2012-10-30
hmmm jmull   how hard would this be  ?   

xu&#592;&#613;&#647;    p&#305;&#592;&#633;&#607;&#592; &#623;,&#305; &#477;&#623; &#633;o&#607; p&#633;&#592;&#613; oo&#647;    dl&#477;&#613; &#477;sl&#477; &#477;uo&#654;u&#592; &#633;o no&#654; plno&#596;



this i take it?



> <html> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<title>How to Type Upside Down - Make your text upside down!</title> 
<meta name="description" content="Type upside down - Text generator to create upside down text! Anything you type will become upside down. Use for names, blogs, Facebook, MySpace, etc."> 
<meta name="keywords" content="type upside down,how to type upside down,inverted text, reverse your text, upsidedown text, invert title, write upside down, mirror text, reverse, backwards text, inverted writing, inverted symbols"> 
<meta name="title" content="How to type Upside Down - make your text upside down!" /> 
<link rel="image_src" href="type_upside_down.jpg" alt="how to type upside down" /> 
<link href="style.css" rel="stylesheet" type="text/css" /> 

<script language="JavaScript"> 
function flip() {
 var result = flipString(document.f.original.value.toLowerCase());
 document.f.flipped.value = result;
}
function flipString(aString) {
 var last = aString.length - 1;
 
 var result = new Array(aString.length)
 for (var i = last; i >= 0; --i) {
  var c = aString.charAt(i)
  var r = flipTable[c]
  result[last - i] = r != undefined ? r : c
 }
 return result.join('')
}
 
var flipTable = {
a : '\u0250',
b : 'q',
c : '\u0254', 
d : 'p',
e : '\u01DD',
f : '\u025F', 
g : '\u0183',
h : '\u0265',
i : '\u0131', 
j : '\u027E',
k : '\u029E',
//l : '\u0283',
m : '\u026F',
n : 'u',
r : '\u0279',
t : '\u0287',
v : '\u028C',
w : '\u028D',
y : '\u028E',
'.' : '\u02D9',
'[' : ']',
'(' : ')',
'{' : '}',
'?' : '\u00BF', 
'!' : '\u00A1',
"\'" : ',',
'<' : '>',
'_' : '\u203E',
';' : '\u061B',
'\u203F' : '\u2040',
'\u2045' : '\u2046',
'\u2234' : '\u2235',
'\r' : '\n' 
}
 
for (i in flipTable) {
  flipTable[flipTable[i]] = i
}
 
</script> 
</head> 
<body><link alt="how to type upside down" href="type_upside_down.jpg" rel="image_src" /> 
<link type="text/css" rel="stylesheet" href="style.css" /> 

 
<link rel="image_src" href="type_upside_down.jpg" alt="how to type upside down" /> 
<link href="style.css" rel="stylesheet" type="text/css" /> 

 
 
<form name="f"> 
<div id="header"> 
	<img src="logo.jpg" /> 
 
    <h1>How to type upside down</h1> 
    <h2>Why would you want to type upside down?</h2> 
    <ul> 
    	<li>Put it in instant messages like MSN, AOL, gTalk</li> 
    	<li>Put upside down text on Twitter, MySpace, MSN Messenger, Facebook, YouTube</li>        
    	<li>Create very strong passwords</li>  
    	<li>Type upside down ... just for fun!</li>   
   </ul><p>        
       <!-- AddThis Button BEGIN --> 
 
<a href="http://www.addthis.com/bookmark.php" onmouseover="return addthis_open(this, '', '[URL]', '[TITLE]')" onmouseout="addthis_close()" onclick="return addthis_sendto()"><img height="16" width="125" border="0" src="http://s7.addthis.com/static/btn/lg-share-en.gif" /></a></p><p> 
<!-- AddThis Button END --> 
 
    
</p></div> 
<div id="content"> 
<div id="contentInner"> 
<div> 
<div class="col1"><img src="yourText.jpg" alt="how to type upside down" />* </div> 
<div class="arrow"><img src="arrow.png" alt="upside down typing" /> </div> 
<div class="col3"><textarea class="textBox" id="original" name="original" onkeyup="flip()">Type your text here...</textarea></div> 
</div> 

<br class="sp" /> 


<div> 
<div class="col1"><img src="flippedtext.jpg" alt="type upside down - inverted text" /> </div> 
<div class="arrow"><img src="arrow.png" alt="how to type upside down" /> </div> 
<div class="col3"><textarea class="textBox" id="flipped" name="flipped"></textarea></div> 

</div> 
<br class="sp" /> 

</div>   
</div> 
<div id="footer"> 
  
<table width="600" border="0"> 
<tbody><tr><td valign="middle"><div align="center">(c)2008-2009  TypeUpsideDown.com 
        <br /> 
        </div></td> 
</tr> 
  </tbody></table> 
 <br /> 
 
  
  </div> 
 
 
</form>

<script type="text/javascript">
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
</script>
<script type="text/javascript">
try {
var pageTracker = _gat._getTracker("UA-5858337-7");
pageTracker._trackPageview();
} catch(err) {}</script>

</body> 
</html>

---

### Post by jmull on 2012-10-30
Someone better at scripting than me and with more time would probably be able to help more. But it shouldn't be hard to convert it to python. If you really want to do it you I would suggest looking up equivalent stuff and just doing it, even if it doesn't work right away at least you learn something new and know how to make changes. If basically just associates every letter of the alphabet with a unicode character and runs through the input to replace them from a simple array.

---

### Post by drmrgd on 2012-10-30
My Python skills are rusty (read=non-existent).  But, this would be fairly simple to re-write in Python.  It looks like the author has defined a dictionary of letters to its affiliated unicode upside down version.  Then they're reading in the text, converting it to lowercase (in order to make it more simple...I'll gather you can't get upside down upper-case letters with this code), then iterating over the string (stored in an array) and looking up the equivalent unicode upside down character from the dictionary (or hash table I suppose) that was built. 

So, you'll just need to build a similar dictionary (probably just copy that one), and figure out how to read in a string and store it to an array.  Finally, you'll iterate over that array using each character of the string as a key way to get the associated value in a similar way.

---

### Post by shantiq on 2012-10-31
i found this in my travels

> OpenOffice Writer
9

Open the Drawing toolbar in OpenOffice Writer by selecting "View," "Toolbars" and "Drawing."
10

Click the "Text" button from the "Drawing" toolbar. Then drag a text box across your page in the area where you want it to go. A cursor will flash within the text box.
11

Begin typing the text you want to rotate. Press the "Escape" key when you are finished. The text box will be selected.
12

Go to the "Drawing Object Properties" toolbar at the top of your page, and click on the "Rotate" icon.
13

Place your mouse over one of the corners of the text box. A rotation handle will appear. Rotate the text box by turning the handle until its contents are flipped upside down.


but i see no way to copy and paste it elsewhere   it remains in the box    and only works if kept as a document there only i do not fully understand how it is done


i see no way to FLATTEN the created upside down text to then copy it and paste in say a text editor or Facebook message



so my question remains    any of you know better?



**ps**   also found this   > Launch your Web browser and navigate to WriteUpsideDown.net, FlipText.org or TypeUpsideDown.com.   but not ubuntu solution

---

### Post by Lars Noodén on 2012-10-31
> **shantiq said:**
> hmmm jmull   how hard would this be  ?   


The only hard part is gathering the data for the lookup table.  After that, it is just processing the input with a hash.

```

#!/usr/bin/perl

use strict;
use warnings;
use utf8;

binmode(STDOUT, ":utf8");

my %flipTable = (
    "a" => "\x{0250}",
    "b" => "q",
    "c" => "\x{0254}", 
    "d" => "p",
    "e" => "\x{01DD}",
    "f" => "\x{025F}", 
    "g" => "\x{0183}",
    "h" => "\x{0265}",
    "i" => "\x{0131}", 
    "j" => "\x{027E}",
    "k" => "\x{029E}",
    "l" => "l",
    "m" => "\x{026F}",
    "n" => "u",
    "o" => "o",
    "p" => "d",
    "q" => "b",
    "r" => "\x{0279}",
    "s" => "s",
    "t" => "\x{0287}",
    "v" => "\x{028C}",
    "w" => "\x{028D}",
    "y" => "\x{028E}",
    "." => "\x{02D9}",
    "[" => "]",
    "(" => ")",
    "{" => "}",
    "?" => "\x{00BF}", 
    "!" => "\x{00A1}",
    "\"" => ",",
    "<" => ">",
    "_" => "\x{203E}",
    ";" => "\x{061B}",
    "\x{203F}" => "\x{2040}",
    "\x{2045}" => "\x{2046}",
    "\x{2234}" => "\x{2235}",
    "\r" => "\n",
    " " => " "
);

while ( <> ) {
    my $string = reverse( $_ );
    while ($string =~ /(.)/g) {
	print $flipTable{$1};
    }
    print qq(\n);
}


```

The above might be incomplete.  Just toss the needed substitutions into the hash.

---

### Post by shantiq on 2012-10-31
first of all Lars thank you:KS   but this is way over my head   [ i could not program myself out of a room with a huge fluorescent sign saying this way out :::]]]


how to use this?

**=========================**

i also found some [**upside down fonts on the net**]("http://www.fontpalace.com/font-download/UpsideDown/")   [**also**]("http://www.fonts2u.com/quirkus-upside-down.font")

and they can be used to write and save  a .doc or .txt  or pdf  but of course

it all falls down when one tries to copy and paste into a message on the net

¡&#633;&#477;&#623;&#623;nq

---

### Post by Lars Noodén on 2012-10-31
> **shantiq said:**
> how to use this?


Put it in a file called flip.pl in the directory ~/bin/
You might have to create the directory.  Then right click on it and set 'Allow executing file as program'

Then open a terminal (ctrl-alt-t) and type 'flip.pl'  Enter any text you like and press enter.

---

### Post by shantiq on 2012-10-31
okmight be me   but this is what i get

[ATTACH]226453[/ATTACH]


and then 


> shantiq@shantiq-00000000000000000000000:~$ flip.pl
bash: /bin/flip.pl: No such file or directory
shantiq@shantiq-00000000000000000000000:~$ 


[B]
ok got it  !!!!!!!!!!!!!!![/B]


needs to go into    /bin/      and not ~/bin/




> sudo mv flip.pl /bin/
cd /bin/
sudo chown +x flip.bin



then all good !!!!!!!!!!!!!!!      thanx a bunch     your script  will help others too no doubt...

---

### Post by Lars Noodén on 2012-10-31
Hmm.  You can always call it with a path. Either of the following should work, if it's in the right place.

```

/home/shantiq/bin/flip.pl

~/bin/flip.pl

```

---

### Post by shantiq on 2012-10-31
yes i see   teaches me about the way it is all rigged up

will leave in in /bin/ safer for me tucked out of the way


excellent!:KS


2 or 3 letters added l z u ' , x




> #!/usr/bin/perl

use strict;
use warnings;
use utf8;

binmode(STDOUT, ":utf8");

my %flipTable = (
    "a" => "\x{0250}",
    "b" => "q",
    "c" => "\x{0254}", 
    "d" => "p",
    "e" => "\x{01DD}",
    "f" => "\x{025F}", 
    "g" => "\x{0183}",
    "h" => "\x{0265}",
    "i" => "\x{0131}", 
    "j" => "\x{027E}",
    "k" => "\x{029E}",
    "l" => "\x{0283}",
    "m" => "\x{026F}",
    "n" => "u",
    "o" => "o",
    "p" => "d",
    "q" => "b",
    "r" => "\x{0279}",
    "s" => "s",
    "t" => "\x{0287}",
    "u" => "n",
    "v" => "\x{028C}",
    "w" => "\x{028D}",
    "x" => "x",
    "y" => "\x{028E}",
    "z" => "z",
    "A" => "\x{0250}",
    "B" => "q",
    "C" => "\x{0254}", 
    "D" => "p",
    "E" => "\x{01DD}",
    "F" => "\x{025F}", 
    "G" => "\x{0183}",
    "H" => "\x{0265}",
    "I" => "\x{0131}", 
    "J" => "\x{027E}",
    "K" => "\x{029E}",
    "L" => "\x{0283}",
    "M" => "\x{026F}",
    "N" => "u",
    "O" => "o",
    "P" => "d",
    "Q" => "b",
    "R" => "\x{0279}",
    "S" => "s",
    "T" => "\x{0287}",
    "U" => "n",
    "V" => "\x{028C}",
    "W" => "\x{028D}",
    "X" => "x",
    "Y" => "\x{028E}",
    "Z" => "z",
    "." => "\x{02D9}",
    "[" => "]",
    "'" => ",",
    "," => "'",
    "(" => ")",
    "{" => "}",
    "?" => "\x{00BF}", 
    "!" => "\x{00A1}",
    "\"" => ",",
    "<" => ">",
    "_" => "\x{203E}",
    ";" => "\x{061B}",
    "\x{203F}" => "\x{2040}",
    "\x{2045}" => "\x{2046}",
    "\x{2234}" => "\x{2235}",
    "\r" => "\n",
    " " => " "
);

while ( <> ) {
    my $string = reverse( $_ );
    while ($string =~ /(.)/g) {
	print $flipTable{$1};
    }
    print qq(\n);
}


[FONT="Century Gothic"]not sure where to fish out **the Capitals**   Where should i be looking to find the values if at all possible ?   Anyone ?[/FONT]  cheated until i know better   and turned them to lowercase   [see above]




[see here for [**summary**]("http://ubuntuforums.org/showpost.php?p=12327388&postcount=1")]

---

### Post by shantiq on 2012-11-25
all info now in [**wiki **]("https://help.ubuntu.com/community/UsingTheTerminal#How_to_create_upsidedown_and.2BAC8-or_reverse_text_with_your_terminal")

---

### Post by rockrer2215 on 2013-01-05
thanks for share
i know a software named "3dpageflip"have command line tool function. This software can let me use command line language to convert [pdf to flip]("http://www.3dpageflip.com/pageflip-3d-pro/index.html") book with wonderful 3d page turning effect. you can google it.

---


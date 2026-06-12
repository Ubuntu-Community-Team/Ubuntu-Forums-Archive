---
title: "How do I install a new radio station in Rhythmbox?"
date: 2011-02-16
forum: Multimedia Software
---

### Post by Caractacus50 on 2011-02-16
Running Ubuntu exclusively on an Acer laptop and love it. 

But I'm trying to add my own radio station: I find a station I like on the web, and click "listen live" on that station's web site. I copy that URL. I go to Rhythmbox and add a new station, and paste that URL.

When I try to play, a box comes up that says "Search for suitable plug-in?" I say yes and it searches, then says no suitable plugin found.

Is there anything I can do to get that station to play?

---

### Post by Animal X on 2011-02-16
just curious, what is the url that ur adding?

mine is:  

> 
[http://www.1.fm/TuneIn/WM/energy90s128k/Listen.aspx](http://www.1.fm/TuneIn/WM/energy90s128k/Listen.aspx)


and i just put it in and listened to it.

im running:
ubuntu 10.10 on acer aspire 4520 w/tk-55 proc ?

---

### Post by Caractacus50 on 2011-02-17
Animal X: The link you provided works fine. But any station I find on the internet that plays through my browser won't work in Rhythmbox. Here is one typical example

[http://www.1170kfaq.com/kfaqplayer.html](http://www.1170kfaq.com/kfaqplayer.html)

---

### Post by Animal X on 2011-02-24
ok, it's not going to work, here's why...


when you:

> wget [http://www.1.fm/TuneIn/WM/energy90s128k/Listen.aspx](http://www.1.fm/TuneIn/WM/energy90s128k/Listen.aspx)

then open it with gedit you see:

> <ASX version = "3.0">
<TITLE>1.FM</TITLE>
<MoreInfo href = "http://www.1.fm" />
<Entry>
      <Ref href = "http://tai.egihosting.com:80/90s-128k-mp3" />      
      <PARAM NAME="HTMLView" Value="http://www.1.fm/station/90s/Listen.aspx"/>
</Entry>
<Entry>
      <Ref href = "http://tai.egihosting.com:80/90s-128k-mp3" />     
      <PARAM NAME="HTMLView" Value="http://www.1.fm/station/90s/Listen.aspx"/>
</Entry>
<Entry>
      <Ref href = "http://tai.egihosting.com:80/90s-128k-mp3" />      
      <PARAM NAME="HTMLView" Value="http://www.1.fm/station/90s/Listen.aspx"/>
</Entry>
</ASX>


notice where it has :80 and mp3 ? thats what you need on your stuff.....

now...


> wget [http://www.1170kfaq.com/kfaqplayer.html](http://www.1170kfaq.com/kfaqplayer.html)

gives you:

> <html>
<head>
<title>KFAQ-AM Streaming Player</title>
</head>
<style type="text/css"> 
<!--
body {
	background-color: #262626;
	margin: 0;
}
#flashPlayer
{
	position:absolute;
	left:80px;
	top:132px;
	width:600px;
	height:296px;
	display:block;
	z-index: 1;
}
#adExternal_bigbox
{
	position:absolute;
	left:376px;
	top:152px;
	width:300px;
	height:250px;
	background-color:#000000;
	display:block;
	z-index: 1000;
}
-->
</style>

<table id="Table_01" width="680" border="0" cellpadding="0" cellspacing="0"> 
	<tr> 
        <td colspan="2"><a href="http://www.1170kfaq.com" target="_blank"><img src="images/streamHeader.jpg" border="0" width="680" height="131" alt="KFAQ"></a></td> 
	</tr> 
    <tr> 
			<td rowspan="2" width="80"><a href="http://www.lakecountrychevrolet.com/new_inventory.php?TSID=175468&res_sort=21111-A&search_price_min=&search_price_max=&search_Make=CHEVROLET&search_Model=SILVERADO+1500&search_Trim=&search_VehicleType=&search_Body=&search_StockNumber=" target="_blank"><img src="ads/kfaq_streamer_leftbar.jpg" border="0" alt=""></a></td> 
			<td width="600" height="296">
				<script src="http://player.streamtheworld.com/_core/adexternal.php?type=bigbox" type="text/javascript" language="javascript"></script>
				<div id="flashPlayer">
					<script src="http://player.streamtheworld.com/liveplayer.php?template=js&callsign=KFAQAM&wmode=transparent" type="text/javascript" language="javascript"></script>
				</div>
			</td> 
		</tr> 
    <tr> 
        <td align="left"><a href="http://www.lakecountrychevrolet.com" target="_blank"><img src="ads/kfaq_stream_bottom.jpg" border="0" alt=""></td> 
    </tr> 
</table> 
</body>
</html>


which i reduced to:


> <html>
<head>
<title>KFAQ-AM Streaming Player</title>
</head>
<style type="text/css"> 
<!--
body {
	background-color: #262626;
	margin: 0;
}
#flashPlayer
{
	position:absolute;
	left:80px;
	top:132px;
	width:600px;
	height:296px;
	display:block;
	z-index: 1;
}
#adExternal_bigbox
{
	position:absolute;
	left:376px;
	top:152px;
	width:300px;
	height:250px;
	background-color:#000000;
	display:block;
	z-index: 1000;
}
-->
</style>



<script src="http://player.streamtheworld.com/liveplayer.php?template=js&callsign=KFAQAM&wmode=transparent" type="text/javascript" language="javascript"></script>


which works in the browser still. notice how it doesn't have the :80 or any .mp3 or anything. and if you isolate the link you get a text document with the code that makes it all work, but i dont find references to the file itself. you want to track down every aspect of the website in question until you find the .aspx file or equivalent that points to the port (:80 for example) that has the actual sound file you want. all an aspx file is is a text file with the link to point, but its written in a format that rhythmbox understands(and VLC).

---


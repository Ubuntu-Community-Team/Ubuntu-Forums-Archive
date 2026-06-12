---
title: "How can I record this stream?"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by macey on 2007-10-06
Hi, I have been attempting to record this stream which (as far as I am concerned) has it's source cleverly disguised, probably for copyright reasons: -

[http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#](http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#)

I have tried Sound Recorder and realplayer (cannot decipher source).
Any ideas?

---

### Post by GerryB on 2007-10-06
> **macey said:**
> Hi, I have been attempting to record this stream which (as far as I am concerned) has it's source cleverly disguised, probably for copyright reasons: -

[http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#](http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#)

I have tried Sound Recorder and realplayer (cannot decipher source).
Any ideas?

You can listen with RealPlayer but look at this first
[http://www.bbc.co.uk/radio/help/?focuswin](http://www.bbc.co.uk/radio/help/?focuswin)
especially the link to Linux
I hope this helps.

---

### Post by macey on 2007-10-06
No, it doesn't help me in the slightest. I know I can LISTEN with Realplayer, I want to RECORD the stream. I know I could resort to Windows Moviplayer to record the Realplayer stream. Want to do the same with Ubuntu/Linux.

---

### Post by GerryB on 2007-10-07
> **macey said:**
> No, it doesn't help me in the slightest. I know I can LISTEN with Realplayer, I want to RECORD the stream. I know I could resort to Windows Moviplayer to record the Realplayer stream. Want to do the same with Ubuntu/Linux.

Since I'm the only guy answering, I'll try to help. Here is something else:
[http://blog.firetree.net/2005/09/23/recording-from-realplayer/](http://blog.firetree.net/2005/09/23/recording-from-realplayer/)
Can you record any other stream in RealPlayer?

---

### Post by GerryB on 2007-10-08
> **macey said:**
> Hi, I have been attempting to record this stream which (as far as I am concerned) has it's source cleverly disguised, probably for copyright reasons: -

[http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#](http://www.bbc.co.uk/radio/aod/networks/wservice/aod.shtml?wservice/closeup#)

I have tried Sound Recorder and realplayer (cannot decipher source).
Any ideas?

Me again. This is what the source page gives me:
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html lang="en">
<head>
<!-- anti cache -->
<title>BBC Radio Player - Audio on Demand</title> 
<meta name="robots" content="noindex" />

<script language="javascript" type="text/javascript">
<!--
var AudioStream = "/radio/aod/shows/rpms/wservice/closeup";
var PlayerType = "Music".toLowerCase();
var show_end="2001/01/24";

var Title="Close Up";

var version= "false";
//-->
</script>

<script language="javascript" type="text/javascript" src="/radio/aod/javascript/all.js"></script>
<style type="text/css">
<!--
@import url(/radio/aod/css/all.css?);
@import url(/radio/aod/css/player.css?);
-->
</style>

	<meta name="author" content="British Broadcasting Corporation" />

	<meta http-equiv="content-script-type" content="text/javascript" />
	<meta http-equiv="content-style-type" content="text/css" />
	<meta http-equiv="content-language" content="EN" />

	<!-- rpps publish -->
	<meta name="rpps-version" content="final" />
	
	<!-- rpps file -->
	<meta name="rpps-file-name" content="World Service" />
	

	<!-- rpps group -->

	
	<meta name="rpps-group-type" content="national" />
	<meta name="rpps-group-name" content="wservice" />

</head>
<body onLoad="LoadStart();" onunload="AodStop();">
<table cellpadding="0" cellspacing="0" border="0" id="player">
<tr>
<td valign="top" height="27" class="fill">
<div id="logo">
<img src="/radio/aod/images/log_playertab_nowplayin.gif" alt="BBC Radio Player" width="208" height="21" border="0" align="absmiddle" /><span class="text-up">Browse:</span><br clear="all" />
<img src="/radio/aod/images/log_playertab_base_x.gif" width="266" height="6" alt="" border="0" /></div></td>
</tr>
<tr>
<td class="player" valign="top" height="370">

<div id="display">
<script language="javascript" type="text/javascript" src="/radio/aod/javascript/lang_detect.js"></script>
<script language="javascript" type="text/javascript">
<!--
//do not put into external js - mozilla bug makes extra padding.
var detectableWithVB;
function detectReal(){
    pluginFound = detectPlugin('Real');
    // if not found, try to detect with VBScript
    if(!pluginFound && detectableWithVB){
		pluginFound = (detectActiveXControl('rmocx.RealPlayer G2 Control') || detectActiveXControl('RealPlayer.RealPlayer(tm) ActiveX Control (32-bit)') || detectActiveXControl('RealVideo.RealVideo(tm) ActiveX Control (32-bit)'));
    }
	if(pluginFound==true){
		aBDP[0] = "real:1";
		strBDP=aBDP.join(",");
		setCookie('BBCDetectPlugin',strBDP,'/','180');
	}
    return pluginFound;
}
function detectPlugin(){
    var strPlugin = detectPlugin.arguments;
    var pluginFound = false;
    if (navigator.plugins && navigator.plugins.length > 0) {
 		var pluginsArrayLength = navigator.plugins.length;
 		for (pluginsArrayCounter=0; pluginsArrayCounter < pluginsArrayLength; pluginsArrayCounter++ ) 		{
     		var numFound = 0;
    		for(namesCounter=0; namesCounter < strPlugin.length; namesCounter++) {
				if((navigator.plugins[pluginsArrayCounter].name.indexOf(strPlugin[namesCounter]) >= 0) || (navigator.plugins[pluginsArrayCounter].description.indexOf(strPlugin[namesCounter]) >= 0) ) {
     				 numFound++;
  				}   
     		}
     		// now that we have checked all the required names against this one plugin,
     		// if the number we found matches the total number provided then we were successful
     		if(numFound == strPlugin.length) 
			{
  				pluginFound = true;
  				// if we've found the plugin, we can stop looking through at the rest of the plugins
  				break;
     		}
 		}
    }
    return pluginFound;
} 
// detectPlugin
// check VBScript version; function to detect activeX control
if (isWinIE) 
{
    document.writeln('<script language="VBscript">');
    document.writeln('detectableWithVB = False');
    document.writeln('If ScriptEngineMajorVersion >= 2 then');
    document.writeln('  detectableWithVB = true');
    document.writeln('End If');
    document.writeln('Function detectActiveXControl(activeXControlName)');
    document.writeln('  on error resume next');
    document.writeln('  detectActiveXControl = False');
    document.writeln('  If detectableWithVB Then');
    document.writeln('     detectActiveXControl = IsObject(CreateObject(activeXControlName))');
    document.writeln('  End If');
    document.writeln('End Function');
    document.write('</scr' + 'ipt>');
}
//Run-time test for Real plugin
//var strBDP = getCookie('BBCDetectPlugin');
var aBDP=getCookie('BBCDetectPlugin').split(',');

if(aBDP[0].indexOf('real:1')==-1){
	if (!detectReal() && !ismac45){
		aBDP[0]="real:0";
		strBDP = aBDP.join(",");
		setCookie('BBCDetectPlugin',strBDP,'/','180');
		var message = "You either do not have Real Player or the Real Player plugin installed.\nPlease click ok to see our Audio Help page\nwith instructions on how to install Real Player and the plugin.\nIf you received this message but you do have Real Player and plugin, click Cancel to stop this message appearing again.";	
		if(cymru)
			{message="Nid yw Real Player neu ategyn Real Player wedi ei osod ar eich cyfrifiadur.\nCliciwch OK i weld ein tudalen Cymorth Sain gyda chyfarwyddiadau sut i osod Real Player a'r ategyn. \nOs cawsoch y neges hon a bod Real Player a'r ategyn gennych chi, cliciwch Canslo er mwyn atal y neges hon rhag ymddangos eto."}
		else if(gaidheal)
			{message="Chan eil an dèrna cuid Real Player no plugin Real Player an sès agad. \nBrùth ok airson an duilleag taic fhaicinn far a bheil stiùireadh air mar a chuirear Real Player agus am plugin an gnìomh. \nMa fhuair thu am fios seo agus Real Player agus plugin agad, brùth dubh às airson am fios seo a stad.";}
		if (confirm(message)) 
			{
			//window.opener.location.href='/radio/audiohelp.shtml?focuswin';
			window.open("http://www.bbc.co.uk/radio/audiohelp.shtml?focuswin", 'main');
			}
		else{
			aBDP[0]="real:1";
			strBDP = aBDP.join(",");
			setCookie('BBCDetectPlugin',strBDP,'/','180');
		}
	}
}
//-->
</script>
<div class="line"></div>
<div id="controls">
<table cellpadding="0" cellspacing="0" border="0" width="247">
<tr>
<td rowspan="2" valign="top">
<script language="javascript" type="text/javascript">
<!--
//PLAYBACK CONTROLS
if(!ismac){
		document.write('<embed src="'+AudioStream+'.rpm" type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="0" height="0" name="RP" autostart="true" console="one" nojava="true" />');
	if(!isopera){
		document.write('<img src="/radio/aod/images/pic_ctrlleftbar.gif" width="1" height="30" alt="" border="0" />');
		document.write('<a href="#" onclick="PlayPause();" accesskey="4"><img src="/radio/aod/images/btn_play.gif" width="38" height="30" alt="Play and pause button." border="0" name="playpause" onmousedown="ImgChange(this.name);" /></a>');
		if(PlayerType=="speech"){
			document.write('<a href="#" onclick="Rewind(15);" accesskey="5"><img src="/radio/aod/images/btn_rew15.gif" width="38" height="30" alt="Rewind 15 mins" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="rew15" /></a>');
			document.write('<a href="#" onclick="Rewind(1);" accesskey="6"><img src="/radio/aod/images/btn_rew1.gif" width="38" height="30" alt="Rewind 1 min" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="rew1" /></a>');
			document.write('<a href="#" onclick="FForward(1);" accesskey="7"><img src="/radio/aod/images/btn_fwd1.gif" width="38" height="30" alt="Forward 1 min" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="fwd1" /></a>');
			document.write('<a href="#" onclick="FForward(15);" accesskey="9"><img src="/radio/aod/images/btn_fwd15.gif" width="38" height="30" alt="Forward 15 mins" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="fwd15" /></a>');
		}
		else if(PlayerType=="music"){
			document.write('<a href="#" onclick="FForward(5);" accesskey="8"><img src="/radio/aod/images/btn_fwd5.gif" width="38" height="30" alt="Forward 5 mins" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="fwd5" /></a>');
			document.write('<a href="#" onclick="FForward(15);" accesskey="9"><img src="/radio/aod/images/btn_fwd15.gif" width="38" height="30" alt="Forward 15 mins" border="0" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" name="fwd15" /></a>');
		}
	}
}
if (ismac || isopera){
	document.write('<embed src="'+AudioStream+'.rpm" type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="38" height="30" controls="PlayButton" autostart="true" console="one" nojava="true" />');
	document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="26" height="30" controls="StopButton" console="one" nojava="true" />');
	if(PlayerType=="speech" || PlayerType=="music"){
		if(PlayerType=="speech"){
			document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="16" height="30" controls="RWCtrl" console="one" nojava="true" />');
			document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="126" height="30" controls="PositionSlider" console="one" nojava="true" />');
		}
		document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="16" height="30" controls="FFCtrl" console="one" nojava="true" />');
	}
	document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="20" height="30" controls="VolumeSlider" console="one" nojava="true" />');
}
//-->
</script>
<noscript>
<embed src="/radio/aod/shows/rpms/wservice/closeup.rpm" type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="38" height="30" controls="PlayButton" autostart="true" console="one" nojava="true" accesskey="4" />
<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="26" height="30" controls="StopButton" console="one" nojava="true" />

<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="20" height="30" controls="VolumeSlider" console="one" nojava="true" />
</noscript></td>
<script language="javascript" type="text/javascript">
<!--
//VOLUME
if(!ismac && !isopera){
	document.write('<td align="right">');
	document.write('<a href="#" onclick="VolChange(-20);" accesskey="w"><img src="/radio/aod/images/btn_voldown.gif" width="18" height="19" alt="Volume down 20%" border="0" name="voldown" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" /></a><img src="/radio/aod/images/txi_vol.gif" width="17" height="18" alt="volume" name="voltxt" /><a href="#" onclick="VolChange(20);" accesskey="q"><img src="/radio/aod/images/btn_volup.gif" width="18" height="19" alt="Volume up 20%" border="0" name="volup" onmouseup="ImgChange(this.name);" onmousedown="ImgChange(this.name);" /></a>');
	document.write('</td></tr>');
	document.write('<tr><td align="right">');
	document.write('<img src="/radio/aod/images/pic_vol0.gif" width="53" height="11" alt="Volume indicator" border="0" name="volume" /></td>');
	//CHANGE TO SHOW WELSH
	if(cymru){
		playsrc="/radio/aod/images/btn_chwarae.gif";
		pausesrc="/radio/aod/images/btn_oedi.gif";
		document.images["playpause"].src=playsrc;
		document.images["playpause"].alt="Chwarae / Oedi";
		document.images["voltxt"].src="/radio/aod/images/txi_uchder.gif";
		document.images["voltxt"].alt="Uchder";
		if(PlayerType=="speech"){
			document.images["rew15"].src="/radio/aod/images/btn_ail15.gif";
			document.images["rew15"].alt="Ailweindio 15 min";
			document.images["rew1"].src="/radio/aod/images/btn_ail1.gif";
			document.images["rew1"].alt="Ailweindio 1 mun";
			document.images["fwd1"].src="/radio/aod/images/btn_yml1.gif";
			document.images["fwd1"].alt="Ymlaen 1 mun";
			document.images["fwd15"].src="/radio/aod/images/btn_yml15.gif";
			document.images["fwd15"].alt="Ymlaen 15 min";
		}
		else if(PlayerType=="music"){
			document.images["fwd5"].src="/radio/aod/images/btn_yml5.gif";
			document.images["fwd5"].alt="Ymlaen 5 mun";
			document.images["fwd15"].src="/radio/aod/images/btn_yml15.gif";
			document.images["fwd15"].alt="Ymlaen 15 min";
		}
	}
	//CHANGE TO SHOW SCOT. GAELIC
	else if(gaidheal){
		playsrc="/radio/aod/images/btn_cluich.gif";
		pausesrc="/radio/aod/images/btn_fan.gif";
		document.images["playpause"].src=playsrc;
		document.images["playpause"].alt="Cluich / Fan";
		document.images["voltxt"].src="/radio/aod/images/txi_fuaim.gif";
		document.images["voltxt"].alt="Fuaim";
		if(PlayerType=="speech"){
			document.images["rew15"].src="/radio/aod/images/btn_ais15.gif";
			document.images["rew15"].alt="Air ais luath 15 mion";
			document.images["rew1"].src="/radio/aod/images/btn_ais1.gif";
			document.images["rew1"].alt="Air ais luath 1 mhion";
			document.images["fwd1"].src="/radio/aod/images/btn_adh1.gif";
			document.images["fwd1"].alt="Air adhart luath 1 mhion";
			document.images["fwd15"].src="/radio/aod/images/btn_adh15.gif";
			document.images["fwd15"].alt="Air adhart luath 15 mion";
		}
		else if(PlayerType=="music"){		
			document.images["fwd5"].src="/radio/aod/images/btn_adh5.gif";
			document.images["fwd5"].alt="Air adhart luath 5 mion";
			document.images["fwd15"].src="/radio/aod/images/btn_adh15.gif";
			document.images["fwd15"].alt="Air adhart luath 15 mion";
		}
	}
	else{
		playsrc="/radio/aod/images/btn_play.gif";
		pausesrc="/radio/aod/images/btn_pause.gif";
	}
}
//-->
</script>
</tr>

</table>
</div>
<div class="line"></div>
<div id="status"><layer id="lstatus">
<noscript><embed src="/radio/aod/shows/rpms/wservice/closeup.rpm" type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="237" height="24" controls="StatusBar" console="one" nojava="true" /></noscript>&nbsp;</layer><script language="javascript" type="text/javascript">
<!--
if(ismac || isopera)
	{document.write('<embed type="audio/x-pn-realaudio-plugin" pluginspage="http://www.bbc.co.uk/webwise/askbruce/articles/download/howdoidownloadrealplayer_1.shtml" width="237" height="24" controls="StatusBar" console="one" nojava="true" />');}
//-->
</script></div>
<div class="line"></div>
<table cellpadding="0" cellspacing="0" border="0" width="247">
<tr>
<td width="50%"><div class="statinfo"><script language="javascript" type="text/javascript">
<!--
document.write(statinfo);
//-->
</script><noscript>Now playing Live</noscript></div></td>
</tr>
</table>
<div class="line"></div>
<script language="javascript" type="text/javascript">
<!--
//INTERACT W. AUDIO OBJECT
//image changing functions
function ImgChange(img){
	if(document.images){
		var imgsrc = document.images[img].src;
		var filetype=imgsrc.substring(imgsrc.lastIndexOf("."),imgsrc.length);
		var filename=imgsrc.substring(0,imgsrc.lastIndexOf("."));
		if(filename.indexOf("_on")==-1)
			{document.images[img].src = filename + "_on" + filetype;}
		else{
			filename = filename.substr(0,imgsrc.lastIndexOf("_on"));
			document.images[img].src = filename + filetype;
		}
	}
}
function ImgPlay(){
	if(document.images['playpause'].src.indexOf(playsrc)==-1)
		{document.images['playpause'].src=playsrc;}
}
function ImgPause(){
	if(document.images['playpause'].src.indexOf(pausesrc)==-1)
		{document.images['playpause'].src=pausesrc;}
}
function ImgVol(){
	if(document.images){
		if(document.RP.GetVolume()<=1)
			{document.images['volume'].src='/radio/aod/images/pic_vol0.gif';}
		else if(document.RP.GetVolume()<40)
			{document.images['volume'].src='/radio/aod/images/pic_vol20.gif';}
		else if(document.RP.GetVolume()<60)
			{document.images['volume'].src='/radio/aod/images/pic_vol40.gif';}
		else if(document.RP.GetVolume()<80)
			{document.images['volume'].src='/radio/aod/images/pic_vol60.gif';}
		else if(document.RP.GetVolume()<100)
			{document.images['volume'].src='/radio/aod/images/pic_vol80.gif';}
		else
			{document.images['volume'].src='/radio/aod/images/pic_vol100.gif';}
	}
}
//end image changing
//time setting functions
function TwoChars(num){
	if(num<10)
		{num="0"+num;}
	return num;
}
function TimeConvert(ms){
	var msConvert=new Date(ms);
	var msHours=msConvert.getHours();
	var msMinutes=msConvert.getMinutes();
	var msSeconds=msConvert.getSeconds();
	var msConverted=TwoChars(msHours)+":"+TwoChars(msMinutes)+":"+TwoChars(msSeconds);
	return msConverted;
}
//end time setting
//embedded player functions
function PlayPause(){
	if(!ismac){
		if(eval(document.RP.GetPlayState())==3) {
			ImgPause();
			if (document.RP.CanPause())
				{document.RP.DoPause();}
		}
		else {
			ImgPlay();
			if (document.RP.CanPlay())
				{document.RP.DoPlay();}
		}
	}
}
function Stop(){
	if(!ismac && !isopera){
		if(document.RP.CanStop())
			{document.RP.DoStop();}
	}
}
function AodStop(){
	var dShow_end = new Date(show_end);
	var dNow = new Date();
	dShow_end.setDate(dShow_end.getDate()+7);
	if(dShow_end > 0)
		{dLife = Math.round(eval((dShow_end-dNow)/1000/60/60/24));}
	else
		{dLife = 7;}
	setResume('rmRp'+location.search.substring(1),dLife);
	Stop();
}
function FForward(mins)
	{PosChange(mins);}
function Rewind(mins)
	{PosChange(-mins);}
function PosChange(mins){
	if(!ismac && document.RP.GetCanSeek()){
		newTime = document.RP.GetPosition()+(mins*60000);
		if(newTime>=0 && newTime < document.RP.GetLength())
			{document.RP.SetPosition(newTime);}
	}
}
function VolChange(vol){
	if(!ismac){
		if(document.RP.GetVolume()){
			if(document.RP.GetVolume()>80 && vol>0)
				{document.RP.SetVolume(100);}
			else if(document.RP.GetVolume()<21 && vol<0)
				{document.RP.SetVolume(1);}
			else
				{document.RP.SetVolume(document.RP.GetVolume()+vol);}
		}
		ImgVol();
	}
}
//end embedded player
//report status of Real Player functions
function GetStatus(){
	if(!ismac){
		if(eval(document.RP.GetPlayState())==0){
			if (document.RP.GetLength() != 0 && (document.RP.GetPosition() == document.RP.GetLength()))
				{ImgPlay();}
			strState="Stopped";
		}
		else if(eval(document.RP.GetPlayState())==1){
			ImgPause();
			strState="Contacting...";
		}
		else if(eval(document.RP.GetPlayState())==2){
			ImgPause();
			strState="Loading "+ Math.round((document.RP.GetBufferingTimeElapsed()/1000)*100)/100 + " sec";
		}
		else if(eval(document.RP.GetPlayState())==3){
			ImgPause();
	 		var secs=document.RP.GetBandwidthAverage()/1000;
			strState = "Playing " + Math.round(secs) + "kbps ";
			for(i=strState.length;i<25;i++){
				strState += "&nbsp;";
			}
			strState += TimeConvert(document.RP.GetPosition())+"/"+TimeConvert(document.RP.GetLength());
		}
		else if(eval(document.RP.GetPlayState())==4){
			ImgPlay();
			strState="Paused"
			for(i=strState.length;i<28;i++){
				strState+="&nbsp;"
			}
	strState+=TimeConvert(document.RP.GetPosition())+"/"+TimeConvert(document.RP.GetLength());
		}
		else if(eval(document.RP.GetPlayState())==5){
			strState="Seeking";
		}
		else
			{strState="";}
		return strState;
	}
}
//cross-browser write into status box.
function StatusWrite(text){
	if(!ismac){
		//IE6
    	if (document.getElementById)
			{document.getElementById('status').innerHTML = text;}
		//IE 4/5
		else if (document.all)
			{document.all('status').innerHTML = text;}
		//NN4+
		else if (document.layers){
			document.layers['lstatus'].left=10;
			document.layers['lstatus'].top=52;
			document.layers['lstatus'].document.open();
			document.layers['lstatus'].document.write(text);
			document.layers['lstatus'].document.close();
		}
	}
}
//end report status of real player
//Run-time initialise status reporting
if(!ismac && !isopera){
		setInterval('StatusWrite(GetStatus())',1000);
		setTimeout('ImgVol()',1800);
}
//-->

</script>




<!-- This is a non national network. Pickup Metadata by Javascript -->
<div id="show">
  <div id="preloader" style="background: url('/radio/aod/images/ajax-loader.gif') 0 0 no-repeat; width: 30px; height: 30px; margin: 20px 0 0 110px;"></div>
  <div id="rpps-hack" style="float: left; display: none;"></div>

  <script language="javascript" type="text/javascript">
    var qString = "wservice/closeup";
    var metadataXMLPath = "/radio/aod/rpps-hack/includes/networks/" + getNetworkName(qString) + "/metadata.xml";

    function getNetworkName(str) {
      var network = str.substr(0,str.indexOf("/"))
      return network
    }

    function getRamFileName(str){
      var strt = (str.indexOf("/") + 1);
      var filename = str.substr(strt)
      return filename
      //Does not add file extension.
    }

    function getHTTPObject() {
    	var xhr = false;
    	if (window.XMLHttpRequest) {
    		var xhr = new XMLHttpRequest();
    	} else if (window.ActiveXObject) {
    		try {
    			var xhr = new ActiveXObject("Msxml2.XMLHTTP");
    		} catch(e) {
    			try {
    				var xhr = new ActiveXObject("Microsoft.XMLHTTP");
    			} catch(e) {
    				xhr = false;
    			}
    		}
    	}
    	return xhr;
    }

    function LoadMetadataXML(file) {
      var request = getHTTPObject();
      file = file + "?" + Math.random();
      if (request) {
        request.onreadystatechange = function() {
          parseResponse(request);
        };
        request.open('GET', file, true);
        request.send(null);
      }
    }

    function parseResponse(request) {
      if (request.readyState == 4) {
        document.getElementById('preloader').style.display = "none";
        document.getElementById('rpps-hack').style.display = "block";

        if (request.status == 200 || request.status == 304) {
          var data = request.responseXML;
          getShowDetails(data);
        } else {
          alert("Error occurred, please try again.");
        }
      } else {
        document.getElementById('preloader').style.display = "block";
      }
    }

    function getShowDetails(data) {
      var filename = getRamFileName(qString);
      var numOfNodes = data.getElementsByTagName('programme').length;
      var str = null;
      var nodeProgramme = data.getElementsByTagName('programme');

      var title, description, startTime, startDateTime;
      
      //Nasty browser check, only check for Firefox and Safari as they have whitespace issues with xml. For once IE does something better!
      var isFirefox = navigator.userAgent.match("Firefox");
      var isSafari = navigator.userAgent.match("Safari");
      
      for (var i = 0; i < numOfNodes; i++) {
        var getNodeAttribute = nodeProgramme[i].attributes.getNamedItem('ram_filename').value;
        if (filename == getNodeAttribute) {
          if (isFirefox || isSafari) {
            title = nodeProgramme[i].childNodes[1].childNodes[0].nodeValue;
            description = nodeProgramme[i].childNodes[3].childNodes[0].nodeValue;
            //startTime = nodeProgramme[i].childNodes[5].childNodes[0].nodeValue;
            //startDateTime = nodeProgramme[i].childNodes[7].childNodes[0].nodeValue;
          } else {
            title = nodeProgramme[i].childNodes[0].firstChild.nodeValue;
            description = nodeProgramme[i].childNodes[1].firstChild.nodeValue;
            //startTime = nodeProgramme[i].childNodes[2].firstChild.nodeValue;
            //startDateTime = nodeProgramme[i].childNodes[3].firstChild.nodeValue;
          }
        }
      }

      str = "<div id=\"showtitle\" style=\"float: left; display: block; clear: both;\"><big>" + checkEmpty(title) + "</big><br />";
      str += "<div id=\"description\" style=\"display: block; float: left; clear: both;\"><p style=\"padding: 0; margin: 0;\">" + checkEmpty(description)  + "</p></div>";

      //Replace with first str when date to be added. Also make sure you uncomment the startTime and startDateTime above.
      //str = "<div id=\"showtitle\"><big>" + checkEmpty(title) + "</big><br /><span class=\"txinfo\">Broadcast - " + formatDateTime(startDateTime) + "</span>";

      document.getElementById('rpps-hack').innerHTML = str;
    }

    function formatDateTime(dtStr) {
      //2007-08-23T04:00:00Z
      dtStr = dtStr.replace(/-/g,"/").replace(/T/g," ").replace(/Z/g,"");
      var d = Date.parse(dtStr);
      d = new Date(d);
      return d.toLocaleString().replace(/UTC/g,"").replace(/GMT/g,"");
    }
    
    function checkEmpty(str) {
      if (str == "" || str == null) {
        str = "";
      }
      return str;
    }

    LoadMetadataXML(metadataXMLPath);
  </script>
</div>

</div>
<div class="help"><a class="helpx" href="/radio/audiohelp.shtml?focuswin" target="main"><img src="/radio/aod/images/txi_helpqmark_x.gif" width="9" height="11" alt="" border="0" align="left" hspace="0" /><script language="javascript" type="text/javascript">
<!--
document.write(help);
//-->
</script><noscript>Get help listening</noscript></a></div></td>
</tr>
<tr>
<td height="8" class="player"><img src="/f/t.gif" width="1" height="1" alt="" /></td>
</tr>
</table>
<noframes><a href="/radio/aod/index_noframes.shtml" accesskey="0">Access keys guide and homepage</a>.</noframes>

</body>
</html>
....
If you get a message that it can't decipher page source, there is something missing in the RealPlayer set-up. Is there anything in there that can help you?
I'm going to try recording it now and report back.

---

### Post by wolfen69 on 2007-10-08
have you tried streamripper?

---

### Post by GerryB on 2007-10-10
OK, this is where I'm at. I tried to find a free sound recorder that records off the sound card in XP.  Couldn't find any, so I downloaded Advanced Sound Recorder that gives you 40 seconds to try it out. I connected to the link you gave. The BBC Radio Player works both in XP and Ubuntu - you don't need any other player. This sound recorder worked like a charm. I then tried to find a free equivalent in Linux. No luck. You could record with the VLC or Gnome Sound Recorder if you connected your out source to your in source. (The advantage there is that no other sound would interfere with the recording - pop ups, system warnings, etc...) I don't have a wire for that yet, so I don't know if you can also listen while recording. If you couldn't, you would have to get a split wire that connects to two out sources if you have them. Apparently, KRec would work with any Linux Player so long as it went through ALSA. 
Things to tinker with in the next few days: 1) Streamripper as suggested by Wolfen and 2) KRec.
If anyone knows about a free sound recorder that records off the sound card in Linux, I think we'd have the  solution we're looking for.

---

### Post by Original Brownster on 2007-10-10
Hi there,
The url you want is:

rtsp://rmv8.bbc.net.uk:554/worldservice/closeup.ra

you can record it with mplayer on the command line like

mplayer --dumpstream rtsp://rmv8.bbc.net.uk:554/worldservice/closeup.ra --dumpfile yourname.ra

You might be interested in the program I am writing, It can discover the url that is hidden for you (which is how I got it)  
It works ok but it's not finished, it's written in python and gtk so you get a nice gui.

it uses mplayer to download the streams and can even convert it to mp3 and ogg for you.

[IMG]http://farm3.static.flickr.com/2081/1532460449_3e95899963.jpg[/IMG]
If you are interested let me know and I'll send you a copy to test, I can help you set it up and it would be good for me to know what issues you have installing it before I put it up for general download.

You can also use vsound with realplay to record the stream, I'm sure I did this in the past.

---

### Post by chiefoldmist on 2007-10-10
Wayne,

I would be very interested in trying this out for you - can't record Dirk Gently and it is driving me nuts!

COM

---

### Post by Original Brownster on 2007-10-10
I have put together the files and some brief instructions on how to install etc.
I'll try my best to help if you get stuck and it will be good to get some feedback.

Please remember this is alpha stage, it does download realplayer streams ok but I'm sure you'll find bugs!

[http://originalbrownster.awardspace.com/]("http://originalbrownster.awardspace.com/")

---

### Post by GerryB on 2007-10-13
> **Original Brownster said:**
> I have put together the files and some brief instructions on how to install etc.
I'll try my best to help if you get stuck and it will be good to get some feedback.

Please remember this is alpha stage, it does download realplayer streams ok but I'm sure you'll find bugs!

[http://originalbrownster.awardspace.com/]("http://originalbrownster.awardspace.com/")

I'll probably try your program out sometime also. Also, will try Vsound. Nice that you can get the URL..Thanks for the suggestions.

---

### Post by Original Brownster on 2007-10-13
I forgot to say about the program, I guess one of the nice features is the 'auto discovery' routine I built in. Basically I use tcpdump as a network packet sniffer and find the url's that way so it doesn't matter how well the url is hidden :)
The downside if there is one is tcpdump is normally run as root and therefore you have to either run the program as root (which I dont recommend) or you set up your sudoers file so that you can run tcpdump as a user and without entering your password. I guess I should try and write the sniffer routines myself :rolleyes:

It can handle ram files (easy as the url is inside anyway) and ra  / rm files. If you download a realplay movie, you can convert it to mp3 / ogg and just get the audio stream sometimes useful.

Oh and the program converts on the fly using pipes so it doesn't create a massive wav file - useful if your recording a big file.

I've still got to add a timer feature so you can set it off at a certain time and for a specific duration which I think will be useful.

---

### Post by hessiess on 2007-10-13
if you can play it, you can record it;) just use a cable between the specker output and the microphone input, and use a sound recorder program

---

### Post by Original Brownster on 2007-10-14
> **hessiess said:**
> if you can play it, you can record it;) just use a cable between the specker output and the microphone input, and use a sound recorder program

I'd be interested to know if you have done this and what sort of quality you get? I'm guessing you have a 3.5 -> 3.5 jack lead which you simply loop around?
Sure makes it easy :)

---

### Post by VON_CAPO on 2007-10-14
> **Original Brownster said:**
> Hi there,
The url you want is:

rtsp://rmv8.bbc.net.uk:554/worldservice/closeup.ra

you can record it with mplayer on the command line like

mplayer --dumpstream rtsp://rmv8.bbc.net.uk:554/worldservice/closeup.ra --dumpfile yourname.ra

You might be interested in the program I am writing, It can discover the url that is hidden for you (which is how I got it)  
It works ok but it's not finished, it's written in python and gtk so you get a nice gui.

it uses mplayer to download the streams and can even convert it to mp3 and ogg for you.

[IMG]http://farm3.static.flickr.com/2081/1532460449_3e95899963.jpg[/IMG]
If you are interested let me know and I'll send you a copy to test, I can help you set it up and it would be good for me to know what issues you have installing it before I put it up for general download.

You can also use vsound with realplay to record the stream, I'm sure I did this in the past.

This soft made my day. It is really nice.
Thanks. :)

---

### Post by Original Brownster on 2007-10-15
> **VON_CAPO said:**
> This soft made my day. It is really nice.
Thanks. :)

Great thanks for the feedback :) Did you find it easy to install following the instructions?

---

### Post by ThrashJazzAssassin on 2007-10-31
I'm loving your streambank app. getting it to run was easy enough but I wasn't confident in editing the sudoers file and the default save path is a little odd. Also there seems to be no way to change the compression settings. This app should be in the repo's.

---

### Post by Original Brownster on 2007-11-04
> **ThrashJazzAssassin said:**
> I'm loving your streambank app. getting it to run was easy enough but I wasn't confident in editing the sudoers file and the default save path is a little odd. Also there seems to be no way to change the compression settings. This app should be in the repo's.

Thanks, glad you like it, and the feed back too. 
I'm not sure about the best way to make it easier re editing the sudoers file. another option I will look into is prompting for the root password, that way the program will still run as a user but use root to run tcpdump only as this would be preferable to running the program as root. 
I will add some options to make it easy to change compression settings in a future release, along with some form of timer facility.
The default save path is weird, I will change it, something specific to my set up :)

---

### Post by efilnikufecin on 2007-11-12
There is already a program out there to do exactly what you want.  It is called Streambox VCR.  It was made back in 1999 by this company called Streambox([www.streambox.com](www.streambox.com)).  Streambox discontinued development of the program due to a lawsuit brought upon it by Real([www.real.com](www.real.com)).  It was made for Windows.  Regardless, it operates perfectly in Linux using Wine.  It records rtsp, smil, pnm mms, & http streams.  It is your all-in-one download manager.  A real fine piece of programming, I must say.  Obviously, you cannot download the program from [www.streambox.com](www.streambox.com) anymore due to the above-stated reasons.  But, if you do a Google search, you can find a place to download the program.

---

### Post by efilnikufecin on 2007-11-12
Oh yeah, a really good forum you can visit to find ways to record streaming media is [http://p069.ezboard.com/bstreemeboxvcr](http://p069.ezboard.com/bstreemeboxvcr) .

---


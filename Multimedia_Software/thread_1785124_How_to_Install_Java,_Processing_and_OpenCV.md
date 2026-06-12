---
title: "How to Install Java, Processing and OpenCV"
date: 2011-06-17
forum: Multimedia Software
---

### Post by Cristina Amazonas on 2011-06-17
Hi

I'm starting to use Ubuntu 10.04 LTS and want to install a Java based language, Processing which uses OpenCv library to perform video issues.
[http://processing.org/](http://processing.org/)

I'm a begginner at Ubuntu and would appreciate all the help yo can give me.
I'm not familiar with the terminal but willing to be.

I'm also not familiar with the file system, I mean I don't exactly know where the archives downloaded are and where they should be to be executed.

it would be great if I coud just click a script ... (laughs) has anyone made one yet ?

Thanks so much !
Cristina

---

### Post by Toz on 2011-06-18
It's actually quite easy. Here is how:

Step 1: Open a Terminal window (command prompt) window

Step 2: Type in:```
wget http://processing.googlecode.com/files/processing-1.5.1-linux.tgz
```(let it finish downloading)

Step 3: Type in:```
tar xzvf processing-1.5.1-linux.tgz
```

It is now installed into a folder called **processing-1.5.1**. To run the program:```
cd processing-1.5.1
./processing
```

---

### Post by Cristina Amazonas on 2011-06-20
Thanks Toz !
it's kind of working ... but how can I make it show up on the applications menu to make it more acessible to run ?
Also ... there is a data folder somewhere inside the processing folder that I could not find :/

I'm not shure if I've worked before with another version of Processing but it was simple to find the examples. There was a folder for them and inside each example there was a data folder where the images used where stored. Right now I did search for the images used on examples, found them but I couldn't see the path. how can I see it ?

Any hints to install OpenCV library ??

---

### Post by Toz on 2011-06-20
> **Cristina Amazonas said:**
> Thanks Toz !
it's kind of working ... but how can I make it show up on the applications menu to make it more acessible to run ?
Create a file in your ~/.local/share/applications folder called **processing.desktop** will the following contents:
```
[Desktop Entry]
Name=Processing
GenericName=Processing
Comment=Processing
Exec=~/.processing-1.5.1/processing
Icon=gnome-monitor
Terminal=false
Type=Application
Categories=Application;Graphics;

```(feel free to specify another icon). It will show up in your Graphics menu group.

> Also ... there is a data folder somewhere inside the processing folder that I could not find :/

I'm not shure if I've worked before with another version of Processing but it was simple to find the examples. There was a folder for them and inside each example there was a data folder where the images used where stored. Right now I did search for the images used on examples, found them but I couldn't see the path. how can I see it ?
There seem to be some examples in the **modes/java/examples** and **modes/android/examples** folders. Also, if you look in the File menu of the Processing application, there is an Examples submenu that seems to list many of them.

> Any hints to install OpenCV library ??I'm not exactly sure what the OpenCV library is. However, if you open up the Software Centre and filter on opencv, you'll see a number of packages including "libcv2.1 - computer vision library" and "libcvaux2.1 - computer vision extension library". Assuming they are the ones you want, then select the ones you want and install.

---

### Post by Cristina Amazonas on 2011-06-20
Hi Tod

Thanks so much for yur pacient ! I'm using gedit to create the file, but couldn't find  the folders you've mentioned ... Should I create the file in the terminal ? How ? This wil make Processing unexecutable on terminal ?

I've found the examples and images on Processing, ... but this version seems less inttuitive. Anyway Is there any Tools option to specify the view of the path of a searched file ?

About the OpenCV ... it is not that easy to install for Processing to use. I've tried before with no suceed. Someone sent me a step-by-step with other installing programs and using terminal that I could not follow ... I'll try and find it again and post heere soon.

Thanks !

---

### Post by Toz on 2011-06-20
> **Cristina Amazonas said:**
> Hi Tod

Thanks so much for yur pacient ! I'm using gedit to create the file, but couldn't find  the folders you've mentioned ...
Should I create the file in the terminal ? How ? This wil make Processing unexecutable on terminal ?The .local folder is hidden. Make sure you have "Show hidden files" enabled in your file manager.

> I've found the examples and images on Processing, ... but this version seems less inttuitive. Anyway Is there any Tools option to specify the view of the path of a searched file ?I'm sorry, but I have never used the program itself and am unfamiliar with what it does and how it operates.

> About the OpenCV ... it is not that easy to install for Processing to use. I've tried before with no suceed. Someone sent me a step-by-step with other installing programs and using terminal that I could not follow ... I'll try and find it again and post heere soon.
Again, sorry but I've never used this application before. I just did a quick search on google and found this link ([http://createdigitalmotion.com/2009/02/processing-tutorials-getting-started-with-video-processing-via-opencv/]("http://createdigitalmotion.com/2009/02/processing-tutorials-getting-started-with-video-processing-via-opencv/")) that discusses processing and opencv. I hope it helps.

---

### Post by Daedalus6 on 2011-06-26
I am assuming you want to use the openCV library for some sort of video processing... to warn you, the default processing video library uses quicktime, and doesn't run on linux. There are some alternative options, but I haven't gotten them to work yet. I'll post back when I figure it out. Hopefully it wont take too long...

---

### Post by Gunix on 2011-11-07
> **Toz said:**
> It's actually quite easy. Here is how:

Step 1: Open a Terminal window (command prompt) window

Step 2: Type in:```
wget http://processing.googlecode.com/files/processing-1.5.1-linux.tgz
```(let it finish downloading)

Step 3: Type in:```
tar xzvf processing-1.5.1-linux.tgz
```It is now installed into a folder called **processing-1.5.1**. To run the program:```
cd /processing-1.5.1
./processing
```

hello.

I have a problem from the step 3.
> processing-1.5.1/modes/android/examples/Basics/Typography/Words/data/Ziggurat-HTF-Black-32.vlw
processing-1.5.1/modes/android/examples/Basics/Typography/Words/Words.pde
processing-1.5.1/modes/android/examples/Basics/Typography/Letters/
processing-1.5.1/modes/android/examples/Basics/Typography/Letters/data/
processing-1.5.1/modes/android/examples/Basics/Typography/Letters/data/CourierNew36.vlw
processing-1.5.1/modes/android/examples/Basics/Typography/Letters/Letters.pde
processing-1.5.1/modes/android/examples/Basics/Shape/
processing-1.5.1/modes/android/examples/Basics/Shape/LoadDisplayShape/
processing-1.5.1/modes/android/examples/Basics/Shape/LoadDisplayShape/data/
processing-1.5.1/modes/android/examples/Basics/Shape/LoadDisplayShape/data/bot1.svg
processing-1.5.1/modes/android/examples/Basics/Shape/LoadDisplayShape/LoadDisplayShape.pde
processing-1.5.1/modes/android/examples/Basics/Shape/GetChild/
processing-1.5.1/modes/android/examples/Basics/Shape/GetChild/data/
processing-1.5.1/modes/android/examples/Basics/Shape/GetChild/data/usa-wikipedia.svg
processing-1.5.1/modes/android/examples/Basics/Shape/GetChild/GetChild.pde
processing-1.5.1/modes/android/examples/Basics/Shape/DisableStyle/
processing-1.5.1/modes/android/examples/Basics/Shape/DisableStyle/data/
processing-1.5.1/modes/android/examples/Basics/Shape/DisableStyle/data/bot1.svg
processing-1.5.1/modes/android/examples/Basics/Shape/DisableStyle/DisableStyle.pde
processing-1.5.1/modes/android/examples/Basics/Shape/ScaleShape/
processing-1.5.1/modes/android/examples/Basics/Shape/ScaleShape/data/
processing-1.5.1/modes/android/examples/Basics/Shape/ScaleShape/data/bot1.svg
processing-1.5.1/modes/android/examples/Basics/Shape/ScaleShape/ScaleShape.pde
processing-1.5.1/modes/android/examples/Basics/Form/
processing-1.5.1/modes/android/examples/Basics/Form/BezierEllipse/
processing-1.5.1/modes/android/examples/Basics/Form/BezierEllipse/BezierEllipse.pde
processing-1.5.1/modes/android/examples/Basics/Form/PieChart/
processing-1.5.1/modes/android/examples/Basics/Form/PieChart/PieChart.pde
processing-1.5.1/modes/android/examples/Basics/Form/Vertices/
processing-1.5.1/modes/android/examples/Basics/Form/Vertices/Vertices.pde
processing-1.5.1/modes/android/examples/Basics/Form/ShapePrimitives/
processing-1.5.1/modes/android/examples/Basics/Form/ShapePrimitives/ShapePrimitives.pde
processing-1.5.1/modes/android/examples/Basics/Form/PointsLines/
processing-1.5.1/modes/android/examples/Basics/Form/PointsLines/PointsLines.pde
processing-1.5.1/modes/android/examples/Basics/Form/Bezier/
processing-1.5.1/modes/android/examples/Basics/Form/Bezier/Bezier.pde
processing-1.5.1/modes/android/examples/Basics/Form/SimpleCurves/
processing-1.5.1/modes/android/examples/Basics/Form/SimpleCurves/SimpleCurves.pde
processing-1.5.1/modes/android/examples/Basics/Form/TriangleStrip/
processing-1.5.1/modes/android/examples/Basics/Form/TriangleStrip/TriangleStrip.pde
processing-1.5.1/modes/android/examples/Basics/Data/
processing-1.5.1/modes/android/examples/Basics/Data/DatatypeConversion/
processing-1.5.1/modes/android/examples/Basics/Data/DatatypeConversion/DatatypeConversion.pde
processing-1.5.1/modes/android/examples/Basics/Data/VariableScope/
processing-1.5.1/modes/android/examples/Basics/Data/VariableScope/VariableScope.pde
processing-1.5.1/modes/android/examples/Basics/Data/IntegersFloats/
processing-1.5.1/modes/android/examples/Basics/Data/IntegersFloats/IntegersFloats.pde
processing-1.5.1/modes/android/examples/Basics/Data/CharactersStrings/
processing-1.5.1/modes/android/examples/Basics/Data/CharactersStrings/CharactersStrings.pde
processing-1.5.1/modes/android/examples/Basics/Data/CharactersStrings/data/
processing-1.5.1/modes/android/examples/Basics/Data/CharactersStrings/data/rathausFrog.jpg
processing-1.5.1/modes/android/examples/Basics/Data/CharactersStrings/data/Eureka-90.vlw
processing-1.5.1/modes/android/examples/Basics/Data/TrueFalse/
processing-1.5.1/modes/android/examples/Basics/Data/TrueFalse/TrueFalse.pde
processing-1.5.1/modes/android/examples/Basics/Data/Variables/
processing-1.5.1/modes/android/examples/Basics/Data/Variables/Variables.pde
processing-1.5.1/modes/android/examples/Basics/Web/
processing-1.5.1/modes/android/examples/Basics/Web/LoadingImages/
processing-1.5.1/modes/android/examples/Basics/Web/LoadingImages/LoadingImages.pde
processing-1.5.1/modes/android/examples/Basics/Web/EmbeddedLinks/
processing-1.5.1/modes/android/examples/Basics/Web/EmbeddedLinks/EmbeddedLinks.pde
processing-1.5.1/modes/android/examples/Sensors/
processing-1.5.1/modes/android/examples/Sensors/Accelerometer/
processing-1.5.1/modes/android/examples/Sensors/Accelerometer/Accelerometer.pde
processing-1.5.1/modes/android/examples/Sensors/Accelerometer/AccelerometerManager.java
processing-1.5.1/modes/android/examples/Sensors/Compass/
processing-1.5.1/modes/android/examples/Sensors/Compass/CompassManager.java
processing-1.5.1/modes/android/examples/Sensors/Compass/Compass.pde
processing-1.5.1/modes/android/android-core.zip
processing-1.5.1/modes/android/keywords.txt
processing-1.5.1/modes/android/theme/
processing-1.5.1/modes/android/theme/tab-sel-menu.gif
processing-1.5.1/modes/android/theme/tab-unsel-right.gif
processing-1.5.1/modes/android/theme/tab-sel-left.gif
processing-1.5.1/modes/android/theme/tab-unsel-mid.gif
processing-1.5.1/modes/android/theme/tab-unsel-left.gif
processing-1.5.1/modes/android/theme/buttons.gif
processing-1.5.1/modes/android/theme/theme.txt
processing-1.5.1/modes/android/theme/tab-sel-right.gif
processing-1.5.1/modes/android/theme/tab-unsel-menu.gif
processing-1.5.1/modes/android/theme/resize.gif
processing-1.5.1/modes/android/theme/tab-sel-mid.gif
processing-1.5.1/tools/
processing-1.5.1/tools/Mangler/
processing-1.5.1/tools/Mangler/src/
processing-1.5.1/tools/Mangler/src/Mangler.java
processing-1.5.1/tools/Mangler/tool/
processing-1.5.1/tools/Mangler/make.sh
processing-1.5.1/tools/Mangler/bin/
processing-1.5.1/tools/howto.txt
processing-1.5.1/processing

> alex@alex-desktop:~$ cd /processing-1.5.1
bash: cd: /processing-1.5.1: No such file or directory
alex@alex-desktop:~$ cd /processing-1.5.1
bash: cd: /processing-1.5.1: No such file or directory
alex@alex-desktop:~$ ./processing
bash: ./processing: No such file or directory

---

### Post by Toz on 2011-11-07
Sorry, typo, should be:
```
cd processing-1.5.1
```
I've corrected the original post.

---


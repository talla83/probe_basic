===================
Development Install
===================


**Probe Basic Development Installation Guide**

**1- Install Linuxcnc**

::

    http://www.linuxcnc.org/testing-stretch-rtpreempt/

Select the "linuxcnc-stretch-uspace-amd64-r13.iso" option. you will need to make a bootable dvd or USB thumb drive depending on how you plan to install.  The below software is extremely easy and works flawlessly with linux debian OS images. Below is the link for it. I recommend using 2-4gb USB drive for quicker flashing.

::

    https://www.balena.io/etcher/?ref=etcher_update

Once you have created your flash stick for linuxcnc proceed to install and boot the system. (note: It is advised to have an ethernet cable internet connection during install).  Select the graphical installation option. Follow the steps on screen to complete installation.

After installation, copy the following in the main terminal one line at a time and hit enter, select Y for yes if asked at any point during installation.

::

    sudo apt update

    sudo apt upgrade


**2- Upgrade to LinuxCNC version 2.8**

Copy the following in the main terminal one line at a time and hit enter, select Y for yes if asked at any point during installation.

::

    sudo apt-get update

    sudo apt-get dist-upgrade

    sudo apt-get install dirmngr

    sudo apt-get install software-properties-common

    sudo apt-key adv --keyserver hkp://keys.gnupg.net --recv-key E0EE663E

    sudo add-apt-repository "deb http://buildbot.linuxcnc.org/ stretch 2.8-rtpreempt"

    sudo apt update

    sudo apt upgrade

    sudo apt dist-upgrade


**3- Start Linuxcnc first time**

Now linuxcnc needs to be started for the first time for it to create its directory folders. This can be done by the drop down menu and selecting CNC and then LinuxCNC. After the program has started, you can shut it down and continue below.


**4- Install qtpyvcp dependencies**

Copy the following in the main terminal it is all one line, hit enter, select Y for yes f asked at any point during installation.

::

    sudo apt install python-pyqt5 python-pyqt5.qtquick python-dbus.mainloop.pyqt5 python-pyqt5.qtopengl python-pyqt5.qsci python-pyqt5.qtmultimedia qml-module-qtquick-controls gstreamer1.0-plugins-bad libqt5multimedia5-plugins pyqt5-dev-tools python-dev python-setuptools python-pip git:

::

    sudo apt install qttools5.dev qttools5-dev-tools python-pip


**5- Install qtpyvcp**

Copy the following in the main terminal, hit enter, select Y for yes if asked at any point during installation.

::

    git clone https://github.com/kcjengr/qtpyvcp qtpyvcp

    cd qtpyvcp

    pip install --editable .

    cd

    cd ~/qtpyvcp/pyqt5designer/Qt5.7.1-64bit/

    sudo ./install.sh

    cp ~/qtpyvcp/scripts/.xsessionrc ~/

**IMPORTANT: now Log Off of Linux, then Log In again for the previous installation to take effect, then continue with step 6 after in a main terminal!**


**6- Install probe_basic**

Copy the following in the main terminal, hit enter.

::

    git clone https://github.com/kcjengr/probe_basic.git


**7- Setup the probe_basic directory and install using pip.**

From the main terminal paste the following and press enter after each, if asked, type Y and enter to continue install.

::

    cd probe_basic

    pip install -e .

    cd

    cp -r ~/probe_basic/probe_basic/fonts/ ~/.local/share/

    cp -r ~/probe_basic/config/xyzab/ ~/linuxcnc/configs/
    


**8- Edit probe_basic**

To be able to edit the probe_basic gui, you will enter the following in the main terminal.

::

    editvcp probe_basic


**9- You are Finished with Installation!**

This should complete the installation of QtPyVCP and the probe_basic GUI, you can now run the sim to get to know it, as well open and play with the GUI design.  If you would like to make a Desktop Icon to launch the editor for probe_basic,  follow the below instructions:

right click on the desktop and select "Create Launcher"

In the field entries you can put the following information:

**NOTE: for the command line be sure to change the "YOUR_COMPUTER_NAME_HERE" for you actual computer name, for example /home/jacob/.local/bin/editvcp probe_basic or the launcher will give an error!**

::

    Name: QTDesigner

    Comment: probe_basic gui editor

    Command: /home/YOUR_COMPUTER_NAME_HERE/.local/bin/editvcp probe_basic

    Working Directory:

Press the Save button once completed.

The first launch select Mark Executable when prompted.


**10- Congratualtions you have made it through and should be ready to start having fun!**


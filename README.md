# How-To-Virtualize-MacOS

1. Install VirtualBox

2. Install VirtualBox Extension Pack

    1. Find the right version
    2. Install it

3. Download MacOS VMDK File
    1. http://www.mediafire.com/file/so82y39h9gzpphb/macOS_Catalina_Beta.rar/file
    2. Unrar it using the password 'Geekrar.com' without the quotes

4. Create a new VM in VirtualBox
    1. Name it whatever you want and select Type: Mac OS X and Version Mac OS X (64-bit)
    2. Try to use at least 4gb of RAM
    3. Use an existing virtual hard disk file (the VMDK file you downloaded and extracted earlier)

5. Configure VM
    1. Under System/Motherboard settings -> uncheck the Floppy option from Boot Order
    2. Under System/Processor settings -> Try to select at least 2 processors
    3. Under Display/Screen settings -> Turn Video Memory up as high as you can
    4. Under USB settings -> Select USB 3.0 (You will get a warning here if the Extension Pack is not installed)

6. Commandline Configuration
    1. run the prepare_vm.sh or prepare_vm.bat script included here


### [WINDOWS] BAT SCRIPT:
```cmd
cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage modifyvm "Your VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```


### [UBUNTU] SHELL SCRIPT:
```bash
VBoxManage modifyvm "Your VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "Your VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```

7. Now run the VM
    1. If presented in an endless loop of loading just keep hitting escape until you are kicked out to an UEFI shell
    2. If presented a UEFI screen type "exit" without the quotes and hit enter
    3. In this menu go to Boot Maintenance and select Boot From File
    4. There should be 2 options, the 1st being the loop we were just in, ignore that one and select the 2nd option
    5. Now go down to 'macOS Install Data' and hit enter
    6. Now go down to 'Locked Files' and hit enter
    7. Now go down to 'Boot Files' and hit enter
    8. Now go down to 'boot.efi' and hit enter

8. It will look like it is back in the loop but if you've done everything correctly so far, eventually the mac loading screen will start up and your installation is about to begin!

9. Wait until it finishes, select your preferred options until it is ready.

10. You now have a Mac OS (Catalina) VM.

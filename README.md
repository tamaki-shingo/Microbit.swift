# Microbit.swift
This structure summarizes the service UUID and micro bit characteristics so that it can be handled easily by BLE.
# Usage
## Discovering services
```
    func centralManager(_ central: CBCentralManager, didConnect peripheral: CBPeripheral) {
        let services = [
            CBUUID(string:MicroBit.Service.button.uuid())
            CBUUID(string:MicroBit.Service.eventService.uuid()),
            CBUUID(string:MicroBit.Service.led.uuid()),
            CBUUID(string: MicroBit.Service.uart.uuid()),
        ]
        peripheral.discoverServices(services)
    }
```

##Discovering characteristics
```
    func peripheral(_ peripheral: CBPeripheral, didDiscoverServices error: Error?) {
        peripheral.services?.forEach({ (service) in
            let characteristics: = [
                CBUUID(string: MicroBit.Characteristic.EventService.clientEvent.uuid()),
                CBUUID(string: MicroBit.Characteristic.Led.matrixState.uuid())
                CBUUID(string: MicroBit.Characteristic.Button.button1State.uuid()),
                CBUUID(string: MicroBit.Characteristic.Button.button2State.uuid())
                CBUUID(string: MicroBit.Characteristic.Uart.tx.uuid()),
                CBUUID(string: MicroBit.Characteristic.Uart.rx.uuid())
            ]
            peripheral.discoverCharacteristics(characteristics, for: service)
        })
    }
```

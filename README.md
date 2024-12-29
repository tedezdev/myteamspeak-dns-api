# PHP ile MyTeamSpeak DNS Oluşturma

- MyTeamSpeak'in sağladığı API ile kısa DNS adresleri oluşturabilirsiniz.

## Kullanım Örneği
```php
<?php
require_once ('myteamspeak.class.php');
$teamSpeak = new MyTeamSpeak("examp@example.com", "password");
$list = $teamSpeak->listDns();
if ($list->count > 0) {
    foreach ($list->items as $item) {
        echo "ID: " . $item->id . "<br>";
        echo "Name: " . $item->name . "<br>";
        echo "Host: " . $item->host . "<br>";
        echo "Port: " . $item->port . "<br>";
        echo "-------------------<br>";
    }
} else {
    echo "DNS Bulunamadı";
}

// DNS Oluşturma
$newDns = $teamSpeak->createDns("TedezDev", "127.0.0.1", 9987);
if ($newDns) {
    echo "DNS Oluşturuldu.";
} else {
    echo "DNS Oluşturulamadı.";
}

// DNS Güncelleme
$update = $teamSpeak->updateDns("DNS_ID", "TedezDev", "127.0.0.1", 9987);
print_r($update);

// DNS Silme
$deleteDns = $teamSpeak->deleteDns("DNS_ID");
print_r($deleteDns);

?>

```

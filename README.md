use std::time::Duration;
use std::thread;

fn main() {
    // Tworzenie czasu trwania 2 sekundy
    let two_seconds = Duration::from_secs(2);

    // Możesz również tworzyć czas trwania z milisekund, mikrosekund itp.
    let one_second = Duration::from_millis(1000);

    // Dodawanie czasów trwania
    let three_seconds = two_seconds + one_second;

    // Odejmowanie czasów trwania
    let one_second_again = three_seconds - two_seconds;

    // Użycie czasu trwania z sleep do zatrzymania wykonania
    println!("Sleeping for 2 seconds...");
    thread::sleep(two_seconds);

    // Wypisanie informacji o czasie trwania
    println!("Waited for: {} seconds", two_seconds.as_secs());
    println!("Three seconds: {} seconds", three_seconds.as_secs());
    println!("One second again: {} seconds", one_second_again.as_secs());

    // Symulacja ruchu ośmiornicy
    let mut octopus = Octopus::new();
    octopus.move_randomly();
    println!("Ośmiornica jest teraz na pozycji: ({}, {})", octopus.x, octopus.y);
}

struct Octopus {
    x: i32,
    y: i32,
}

impl Octopus {
    fn new() -> Octopus {
        Octopus { x: 0, y: 0 }
    }

    fn move_randomly(&mut self) {
        let dx: i32 = rand::random();
        let dy: i32 = rand::random();
        self.x = (self.x + dx) % 50; // Zakładamy, że akwarium ma 50x50 jednostek
        self.y = (self.y + dy) % 50;
    }
}

// Мобильное меню
const menuToggle = document.getElementById('menuToggle');
const nav = document.querySelector('nav');

if (menuToggle) {
    menuToggle.addEventListener('click', () => {
        nav.classList.toggle('show');
    });
}

// Плавная прокрутка для ссылок
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
            target.scrollIntoView({
                behavior: 'smooth',
                block: 'start'
            });
            // Закрываем меню на мобильных после клика
            if (nav.classList.contains('show')) {
                nav.classList.remove('show');
            }
        }
    });
});

// Обработка формы
const contactForm = document.getElementById('contactForm');
const formMessage = document.getElementById('formMessage');

if (contactForm) {
    contactForm.addEventListener('submit', function(e) {
        e.preventDefault();
        
        const name = document.getElementById('name').value;
        const email = document.getElementById('email').value;
        const message = document.getElementById('message').value;
        
        if (name && email && message) {
            formMessage.textContent = 'Спасибо! Ваше сообщение отправлено. Мы свяжемся с вами в ближайшее время.';
            formMessage.style.color = '#2c5e2e';
            contactForm.reset();
        } else {
            formMessage.textContent = 'Пожалуйста, заполните все поля.';
            formMessage.style.color = '#e76f51';
        }
        
        setTimeout(() => {
            formMessage.textContent = '';
        }, 5000);
    });
}